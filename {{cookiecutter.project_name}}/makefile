.PHONY:setup_env fetch-and-load latest-csv load-csv publish-cloudrun

setup_env:
	python3 -m venv .venv
	. .venv/bin/activate
	pip install -r requirements.txt
	dbt deps

latest-csv:
	<fill_in>

load-csv:
	sqlite-utils insert data/{{cookiecutter.database_name}}.db <filename> latest.csv --csv --truncate

fetch-and-load: latest-csv load-csv

publish-cloudrun:
	datasette publish\
		cloudrun data/{{cookiecutter.database_name}}.db\
		--service={{cookiecutter.project_name}}-datasette\
		--extra-options='--setting sql_time_limit_ms 100000'\
		--install=datasette-vega
