FROM python:latest

RUN wget https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh -P /
RUN chmod +x /wait-for-it.sh
ENTRYPOINT ["/wait-for-it.sh", "db:5432", "--"]

WORKDIR /usr/src/app

RUN pip3 install psycopg2

ADD data.csv /usr/src/app
COPY config.py /usr/src/app
COPY tests_integration.py /usr/src/app
COPY utils_postgres.py /usr/src/app
COPY _init_.py /usr/src/app
COPY _main_.py /usr/src/app

EXPOSE 5432

CMD ["python", "_main_.py"]