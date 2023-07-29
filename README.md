# DockerIncludeTest  
  
testing the new Docker include feature  
  
## Docker Include  
Ref.: https://github.com/compose-spec/compose-spec/blob/master/14-include.md  
  
## Test Setup  
  
```
/
  docker-compose.yml
  docker-compose.compose_x.merger.yml

  compose_x/
    docker-compose.yml
    docker-compose.merger.yml
  
    service_x/
      docker-compose.yml
```
  
## Goal  
  
independent compose files for each service  
literally: 1 compose file : 1 service  
example: `/compose_a/service_a/docker-compose.yml`  
  
## Approach on include  
  
Included service compose files in a "upstream compose" compose file  
added further configuration using a ".merger.yml" compose file  
  
example:  
`/compose_a/docker-compose.yml`  
will include all "child" compose files and add further configuration via  
`/compose_a/docker-compose.merger.yml`  
  
---  
  
Finally wrapped it again with the same logic  
  
example:  
`/compose_a/docker-compose.yml`  
with having 1 ".merger.yml" for each compose  
example:  
`docker-compose.compose_a.merger.yml`  
  
## Real world example  
Have a look at my other repos: https://github.com/sharedstuff/DockerIncludeExample  