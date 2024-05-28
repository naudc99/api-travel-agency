# Usar una imagen base de JDK 17
FROM openjdk:17-jdk-slim

# Establecer el directorio de trabajo
WORKDIR /app

# Copiar el archivo JAR de la aplicación en el contenedor
COPY target/api-agencia-0.0.1-SNAPSHOT.jar app.jar

# Exponer el puerto en el que la aplicación correrá
EXPOSE 8080

# Comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "app.jar"]