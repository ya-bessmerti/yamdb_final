FROM python:3.7-slim

WORKDIR /app

COPY requirements.txt .

RUN pip3 install -r ./requirements.txt --no-cache-dir

ENV PIP_ROOT_USER_ACTION=ignore

COPY . .

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]
