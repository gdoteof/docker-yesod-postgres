docker with dependencies for running yesod scaffolded for postgres 

must connect with a postgres database explicitly

ie
```
docker build -t yesod-postgres .
docker run --name -d db gdoteof/postgres
docker run -t -i -v /path/to/scaffolded/app/on/host:/code --link db:db yesod-postgres /bin/bash -c "cd /code && yesod devel"
```



