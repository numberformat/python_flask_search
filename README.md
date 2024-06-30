# Search using htmx

## Installation

Create and activate a new environment using conda or python -m venv venv

`conda create -n your_env_name python==3.11`

Activate environment and install the latest dependencies (preferred)

`pip install SQLAlchemy Flask-SQLAlchemy python-dotenv pandas gunicorn`

If project does not work for some reason check requirements.txt which are the libraries this project is known to work with.

Create the schema and import the data

```sh
flask shell

import pandas as pd
from sqlalchemy import create_engine

# create the schema
db.create_all()
df = pd.read_csv("hot100.csv")
df2=df[['title','performer','chart_date','peak_position','weeks_on_chart']]
df3=df2.rename(columns={'weeks_on_chart':'time_on_chart','chart_date':'chart_debut'})
engine = db.get_engine()
df3.index.name='id'
df3.to_sql("song", con=engine, if_exists='append', index=True)
# quit() and query the data to confirm
sqlite3 instance/db.sqlite3
select * from song;
.exit

flask run
```

## How to run on Server

see flask_how_to_run_on_server.md

## Reference

<https://www.youtube.com/watch?v=PWEl1ysbPAY>
