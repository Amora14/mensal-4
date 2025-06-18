# Etapa 1: Build com Maven
FROM maven:3.9.9-eclipse-temurin-17 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

# Etapa 2: Imagem final
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

# Argumentos opcionais no build
ARG DATABASE_URL
ARG DATABASE_USERNAME
ARG DATABASE_PASSWORD

# Exporta as variáveis para o runtime
ENV DATABASE_URL=${DATABASE_URL}
ENV DATABASE_USERNAME=${DATABASE_USERNAME}
ENV DATABASE_PASSWORD=${DATABASE_PASSWORD}

COPY --from=builder /app/target/integrador-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 5000

CMD ["java", "-jar", "app.jar"]
