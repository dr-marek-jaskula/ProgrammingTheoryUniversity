# Dockerfile Important Commands

The `ENTRYPOINT` command appends the command to every docker command. Example

```Dockerfile
FROM Ubuntu

ENTRYPOINT["sleep"]
```

Then `docker run ubuntu-sleeper 10` will result in running `sleep 10` in ubuntu

To add the **default** value to the call we can use `CMD` command in following way:

```Dockerfile
FROM Ubuntu

ENTRYPOINT["sleep"]

CMD["5"]
```

Then `docker run ubuntu-sleeper` will result in running `sleep 5` in ubuntu

In order to override the `ENTRYPOINT` in the runtime we can use

> docker run --entrypoint sleep2.0 ubuntu-sleeper 100

To add options additionally we can use

```Dockerfile
FROM python:3.6-alpine

RUN pip install flask

COPY . /opt/

EXPOSE 8080

WORKDIR /opt

ENTRYPOINT ["python", "app.py"]

CMD ["--color", "red"]
```

To run `python app.py --color red`