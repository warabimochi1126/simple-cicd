FROM gradle:7 AS base

CMD ["bash"]

# test-and-build
FROM base as test-and-build
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# prodution
FROM openjdk:17 AS production
COPY --from=test-and-build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar ./api.jar
CMD [ "java", "-jar", "api.jar" ]