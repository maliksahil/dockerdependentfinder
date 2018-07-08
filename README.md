# Docker Dependent Finder
This little script will help you find dependent docker images, so you'll know exactly which one to delete, so you can delete the parent!

More wordy description can be found at https://winsmarts.com/finding-dependent-docker-images-b0a14b5cf225

Basic usage: 

```
docker images \
    | fgrep -f <(docker inspect --format='{{.Id}} {{.Parent}}' \
        $(docker images --all --quiet) \
        | python3 dependents.py <imageid> )
```

Hope you find it useful!