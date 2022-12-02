.PHONY:fetch-and-load latest-csv load-csv publish-cloudrun

latest-csv:

load-csv:
	sqlite-utils insert data/{{cookiecutter.database_name}}.db <filename> latest.csv --csv --truncate

fetch-and-load: latest-csv load-csv

publish-cloudrun:
	datasette publish\
		cloudrun data/{{cookiecutter.database_name}}.db\
		--service={{cookiecutter.project_name}}-datasette\
		--extra-options='--setting sql_time_limit_ms 100000'\
		--install=datasette-vega