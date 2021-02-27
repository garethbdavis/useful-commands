# useful-commands

## docker

Get all tags for a docker repository - alpine in the example
`wget -q https://registry.hub.docker.com/v1/repositories/alpine/tags -O -  | sed -e 's/[][]//g' -e 's/"//g' -e 's/ //g' | tr '}' '\n'  | awk -F: '{print $3}'`

Create a container with an interactive shell
`docker run -it --entrypoint /bin/sh alpine:latest`

## find/replace

Replace all occurances of a term in a git repo
Linux: `git grep -l 'original_text' | xargs sed -i 's/original_text/new_text/g'`
Mac: `git grep -l 'original_text' | xargs sed -i '' -e 's/original_text/new_text/g'`