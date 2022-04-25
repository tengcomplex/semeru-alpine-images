# Alpine IBM Semeru Test Images
Testing Alpine based Docker images with IBM Semeru Binaries.
Goal is to use OpenJ9 Java 17+ on an Alpine image.

### Additional Information
* https://github.com/ibmruntimes/Semeru-Runtimes/issues/6
* https://hub.docker.com/r/tengcomplex/test-java-images/tags

# Usage
## Build
```
docker build -f Dockerfile-jre17-openj9 -t tengcomplex/test-java-images:alpine-semeru-jre17.0.3 .
docker build -f Dockerfile-jre17-openj9-no-scc -t tengcomplex/test-java-images:alpine-semeru-jre17.0.3-no-scc .
```

## Test
```
docker run --rm -it tengcomplex/test-java-images:alpine-semeru-jre17.0.3 sh -c 'java -version ; ls -latr /opt/java/.scc'
docker run --rm -it tengcomplex/test-java-images:alpine-semeru-jre17.0.3-no-scc sh -c 'java -version ; ls -latr /opt/java/.scc'
```

## Publish
```
docker login --username=yourhubusername --email=youremail@company.com
```

```
docker push tengcomplex/test-java-images:alpine-semeru-jre17.0.3
docker push tengcomplex/test-java-images:alpine-semeru-jre17.0.3-no-scc
```
