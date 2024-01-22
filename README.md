## Nytt dbt prosjekt

### Utvikling
Skriptet [setup_python_env.ps1](https://github.com/navikt/dvh_template/blob/dbt_template/dbt/setup_python_env.ps1) oppretter automatisk et virtuelt python miljø i dbt mappa med navn ```.dbtenv```. Deretter oppdateres pip og nødvendige pakker på [requirements.txt](https://github.com/navikt/dvh_template/blob/dbt_template/dbt/requirements.txt) installeres. Oppdater ønsket versjon av dbt i denne filen før skriptet kjøres.

Aktiver (i Powershell):

``.\.dbtenv\Scripts\activate.ps1``


### Oppsett
- Gi navn til prosjektet i dbt_project.yml
- Opprett en profil i profiles.yml og referer til profilen i dbt_project.yml


For å kjøre dbt prosjektet fra utviklerimage må dbt ha tilgang til secrets for:
- miljø
- komponentskjema
- personlig brukernavn
- personlig passord

Disse secretene settes opp med skriptet `setup_db_user.ps1`, som setter dem som miljøvariabler. Skriptet kjøres fra kommandolinjen og den må kjøres fra dbt folderen fordi skritet også setter pathen for profiles.yml filen.

Eksempel på kjøring:

 ```PS C:\datavarehus\dvh_arb_cv\dbt> ./setup_db_user.ps1```

### Schedulering

dbt_run.py er et skript for schedulere dbt prosjektet i Airflow. Denne filen må endres til å passe sammen med secrets håndteringen til teamet.

### Resources:
- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [chat](https://community.getdbt.com/) on Slack for live discussions and support
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices
