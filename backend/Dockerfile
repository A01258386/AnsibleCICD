FROM python:3

RUN useradd -m -d /app backend 

USER backend 

WORKDIR /app

RUN wget -qq https://github.com/A01258386/AnsibleCICD/raw/main/basefile/acit4640-py-mysql-master.zip -O /tmp/source.zip
RUN unzip /tmp/source.zip
RUN cp -r acit4640-py-mysql-master/backend /app/src
RUN rm -rf acit4640-py-mysql-master

RUN python -m pip install -r /app/src/requirements.txt

WORKDIR /app/src

COPY backend.conf /app/src

EXPOSE 8000

CMD ["/app/.local/bin/gunicorn","wsgi:app" ,"-b", "0.0.0.0:8000"]

