FROM tomcat:8.5-jdk11-openjdk-slim

# Install necessary packages
RUN apt-get update && \
    apt-get install -y git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Clone the WebGoat repository
RUN git clone https://github.com/WebGoat/WebGoat.git

# Build WebGoat
RUN cd WebGoat && \
    git checkout tags/v8.0.0.M25 && \
    ./gradlew war

# Deploy the WebGoat application to Tomcat
RUN cp WebGoat/webgoat-8.0.0.M25.war /usr/local/tomcat/webapps/

# Expose the Tomcat server port
EXPOSE 8080

# Start Tomcat
CMD ["catalina.sh", "run"]