# useful-commands

## docker

Get all tags for a docker repository - alpine in the example
```shell
wget -q https://registry.hub.docker.com/v1/repositories/alpine/tags -O -  | sed -e 's/[][]//g' -e 's/"//g' -e 's/ //g' | tr '}' '\n'  | awk -F: '{print $3}'
```

Create a container with an interactive shell
```shell
docker run -it --entrypoint /bin/sh alpine:latest
```

## kubectl

open a shell into a container in a pod with a specific label
```shell
kubectl exec -it $(kubectl get pods -l "app=my-app" -o jsonpath='{.items[0].metadata.name}') -c my-container -- /bin/sh
```

## find/replace

Replace all occurances of a term in a git repo\
Linux:
```shell
git grep -l 'original_text' | xargs sed -i 's/original_text/new_text/g'
```
Mac:
```shell
git grep -l 'original_text' | xargs sed -i '' -e 's/original_text/new_text/g'
```

## MySQL

Find multi-byte characters
```sql
SELECT * FROM <table> WHERE LENGTH(col) != CHAR_LENGTH(col)
```

## git

undo commit
```shell
git reset HEAD~
```

## disk space

get disk usage of directories:
```shell
du -ch --max-depth=1
```

get disk usage summary:
```shell
df -h
```