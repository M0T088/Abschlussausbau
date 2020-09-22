# spring-boot-webblog

Unter Projektverzeichnis/spring-boot-webblog\src\main\resources\application.properties (in einem Branch)

# 
# All configuration values shall be set through environment variables.
# Those can be defined within Jenkinsfile, Shell Script or similar ways.
#
# A database must be created (!) before starting and using this application.
#

#spring.datasource.url=${SPRING_BOOT_WEBBLOG_DB_URL}

#spring.datasource.username=${SPRING_BOOT_WEBBLOG_DB_USERNAME}
#spring.datasource.password=${SPRING_BOOT_WEBBLOG_DB_PASSWORD}

spring.datasource.url=jdbc:mysql://${MYSQL_HOST:localhost}:3306/db_blog?createDatabaseIfNotExist=true&useUnicode=yes&characterEncoding=UTF-8

spring.datasource.username=root
spring.datasource.password=root

spring.datasource.driver-class-name=com.mysql.jdbc.Driver

spring.jpa.show-sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQL5InnoDBDialect
spring.jpa.properties.hibernate.globally_quoted_identifiers=true

spring.jpa.hibernate.ddl-auto=update

spring.thymeleaf.cache = false
