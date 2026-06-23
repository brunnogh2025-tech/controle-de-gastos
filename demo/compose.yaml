# Etapa 1: Build com Eclipse Temurin JDK 17
FROM eclipse-temurin:17-jdk-jammy as builder
WORKDIR /app
COPY .mvn/ .mvn
COPY mvnw .
COPY pom.xml .
RUN chmod +x mvnw
RUN ./mvnw dependency:go-offline
COPY src ./src
RUN ./mvnw clean package -DskipTests
  
  # Etapa 2: Imagem final com Eclipse Temurin JRE 17 (mais leve)
FROM eclipse-temurin:17-jre-jammy
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]


DB URL → jdbc://neondb_owner:npg_DhKsy8vOl3fV@ep-delicate-math-acixmtxv.sa-east-1.aws.neon.tech/neondb?sslmode=require
DB_USERNAME → neondb_owner
DB_PASSWORD → npg_DhKsy8vOl3fV
