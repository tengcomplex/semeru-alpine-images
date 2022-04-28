# Alpine IBM Semeru Test Images
Testing Alpine based Docker images with IBM Semeru Binaries.
Goal is to use OpenJ9 Java 17+ on an Alpine image.

### Additional Information
* https://github.com/ibmruntimes/Semeru-Runtimes/issues/6
* https://hub.docker.com/r/tengcomplex/test-java-images/tags

# Usage
## Build
```
docker build -f Dockerfile-jre17-openj9-no-scc -t tengcomplex/test-java-images:alpine-semeru-jre17.0.3-no-scc .
docker build -f Dockerfile-jre17-openj9 -t tengcomplex/test-java-images:alpine-semeru-jre17.0.3 .

docker build -f Dockerfile-jre18-openj9-no-scc -t tengcomplex/test-java-images:alpine-semeru-jre18.0.1-no-scc .
docker build -f Dockerfile-jre18-openj9 -t tengcomplex/test-java-images:alpine-semeru-jre18.0.1 .

```

## Test
```
docker run --rm -it tengcomplex/test-java-images:alpine-semeru-jre17.0.3-no-scc sh -c 'java -version ; ls -latr /opt/java/.scc'
docker run --rm -it tengcomplex/test-java-images:alpine-semeru-jre17.0.3 sh -c 'java -version ; ls -latr /opt/java/.scc'

docker run --rm -it tengcomplex/test-java-images:alpine-semeru-jre18.0.1-no-scc sh -c '\
  env | grep "JAVA_VERSION\|JAVA_TOOL_OPTIONS" ; \
  java -version ; \
  ls -latr /opt/java/.scc \
'
docker run --rm -it tengcomplex/test-java-images:alpine-semeru-jre18.0.1 sh -c '\
  env | grep "JAVA_VERSION\|JAVA_TOOL_OPTIONS" ; \
  java -version ; ls -latr /opt/java/.scc ; \
  java -Xshareclasses:name=openj9_system_scc,cacheDir=/opt/java/.scc,printTopLayerStats \
'
```

## Publish
```
docker login --username=yourhubusername --email=youremail@company.com
```

```
docker push tengcomplex/test-java-images:alpine-semeru-jre17.0.3-no-scc
docker push tengcomplex/test-java-images:alpine-semeru-jre17.0.3

docker push tengcomplex/test-java-images:alpine-semeru-jre18.0.1-no-scc
docker push tengcomplex/test-java-images:alpine-semeru-jre18.0.1
```
