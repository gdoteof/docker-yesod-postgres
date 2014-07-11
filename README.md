docker with dependencies for running yesod scaffolded for postgres 

must connect with a postgres database explicitly

ie
```
docker build -t yesod-postgres .
docker run --name -d db gdoteof/postgres
docker run -t -i -v /path/to/scaffolded/app/on/host:/code --link db:db yesod-postgres /bin/bash -c "cd /code && yesod devel"
```


note, gdoteof/postgres comes with a super user ```docker``` with password ```docker``` and a database ```docker```

optionally you can add another database


```docker run -t -i --link db:db yesod-postgres /bin/bash```

then, inside the docker

```apt-get install -y postgresql-client-9.3```

```psql -U docker -h db --command "create database <db_name>"```



additionally, you can extract a scaffolded app

```sudo docker run -d --name yesod-postgres-scaffold yesod-postgres bash -c "tail -f < /dev/null"```
```sudo docker cp yesod-postgres-scaffold:/scratch/scaffold <path_on_host_for_scaffolded_app>```
```sudo docker stop yesod-postgres-scaffold```
```sudo docker rm yesod-postgres-scaffold```

