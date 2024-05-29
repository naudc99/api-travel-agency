
# Usa una imagen base de Maven para construir el proyecto
FROM maven:3.8.6-openjdk-17 AS build

# Establece el directorio de trabajo en /app
WORKDIR /app

# Copia el archivo pom.xml y descarga las dependencias del proyecto
COPY pom.xml .
RUN mvn dependency:go-offline -B

# Copia el código fuente del proyecto
COPY src ./src

# Construye la aplicación
RUN mvn clean package -DskipTests

# Usa una imagen base de OpenJDK para ejecutar la aplicación
FROM openjdk:17-jdk-slim

# Establece el directorio de trabajo en /app
WORKDIR /app

# Copia el JAR desde la imagen de construcción
COPY --from=build /app/target/api-agencia-0.0.1-SNAPSHOT.jar app.jar

# Expone el puerto en el que correrá la aplicación
EXPOSE 8080

# Define el comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "app.jar"]

