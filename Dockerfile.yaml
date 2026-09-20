FROM eclipse-temurin:17-jdk-jammy AS build
WORKDIR /build
COPY . .
RUN ./mvnw clean package -DskipTests

FROM gcr.io/distroless/java17-debian12:nonroot
WORKDIR /app
COPY --from=build /build/target/Spring_Petclinic-*.jar app.jar
EXPOSE 8080
USER nonroot
ENTRYPOINT ["java", "-jar", "app.jar"]
