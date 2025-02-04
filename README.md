# DEZoomcamp2025-Homework
Go to each directory respectively to see the answers, scripts, and screenshots of the outputs/codes.
In this README file, I will display my personal notes for each week.
# Week1
### Setup Notes
1-)First I set up the GCP and ssh
2-) After that I couldn't run ssh de-zoomcamp2025 because in .ssh/config file I did typos. Also check for Byte Order Mark.
3-) I installed anaconda on de-zoomcamp2025 VM Instance, yet, system didn't recognize which python(source to python) which should be "/home/HSY/anaconda3/bin/python".
Then I manually executed "~/anaconda3/bin/conda init bash" and it worked. Reason:
When you ran:
~/anaconda3/bin/conda init bash
it added the necessary initialization commands for Conda into your shell’s startup file (usually ~/.bashrc). 
This ensures that each time you start a new Bash session (or source your ~/.bashrc), Conda’s bin directory is placed on your PATH and its shell functions get loaded.
Before you did this, your shell simply didn’t know where to find conda—it wasn’t in the PATH. 
By running conda init bash, Conda’s installer script updated your environment so that conda commands work automatically in subsequent sessions.
4-) For running Docker on our VM without sudo, "docker without sudo guides"
5-) Install Docker compose v2.20.3
6-) Add docker-compose to path variable nano .bashrc ..> Go all the way to the down and type --> export PATH="${HOME}/bin:${PATH}" ## bin because we have created a bin folder for the executable files and the original docker-compose is there.
7-) "/data-engineering-zoomcamp/01-docker-terraform/2_docker_sql$ docker-compose up -d" pgadmin and postgres files download.
8-) conda install -c conda-forge pgcli
pip install -U mycli
9-) Add port 5432 in vscode to access the docker in local machine(I couldn't)
10-) Add port 8080 and localhost:8080 on browser to access pgadmin
11-) install terraformv1.1.3. , create access token for terraform and add it to the .bashrc
12-) Terraform service account for storage admin, bigquery admin, compute admin
13-) Create json key for service account
14-) Create variables.tf to address the variables in main.tf
15-) Create .gitignore file to prevent credentials being pushed to public
16-) Terraform plan, apply, destroy

### Docker-SQL Notes
1-) Ran docker-compose on the .yaml file to run the postgres on port 5432
2-) Downloaded the parquet file
3-) Import the data on jupyter 
4-) sudo apt update
sudo apt install build-essential for psycopg2
5-) Data is in parquet format. Transform to pandas.dataframe, then transfrom to csv and save it.Approximately 1.5 million rows of data. Upload it to postgres in 100.000 rows chunks.
6-) Upload taxi_zone_lookup from https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv to postgres

### Run PostgreSQL container
docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v /home/HSY/data-engineering-zoomcamp/01-docker-terraform/2_docker_sql/ny_taxi_postgres_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  --network=pg-network \
  --name pg-database \
  postgres:13

docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
  -e PGADMIN_DEFAULT_PASSWORD="root" \
  -p 8080:80 \
  --network=pg-network \
  --name pg-admin \
  dpage/pgadmin4

Week2:
No personal notes, followed the modules.
