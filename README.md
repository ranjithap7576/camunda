# camunda
Camunda related projects

# To start postgres run the docker-compose-dev.yml file

```
  docker-compose -f docker-compose-dev.yml up
```

# Set application properties

Copy the contents of the application-template.yaml file to a new file called application-local.yaml 
and set the properties to your local environment.
```
cp camunda-engine/src/main/resources/application-template.yaml camunda-engine/src/main/resources/application-local.yaml
```
