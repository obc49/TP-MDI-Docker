FROM    ubuntu:16.04

###########################################
MAINTAINER Oumar Roland

###########################################
RUN cd usr/src \
    && apt-get update -y \
    && apt-get upgrade -y

###########################################
# Installing software
RUN apt-get install net-tools \
     && apt-get install -y git \
     && apt-get install -y g++ \
     && apt-get install -y ant \
     && apt-get install -y software-properties-common cmake \
     && apt-get install -y maven \
     && apt-get install -y openjdk-8-jdk \
     && add-apt-repository -y ppa:webupd8team/java \
     && apt-get install -y default-jre \
     && apt-get install -y default-jdk

###########################################
RUN git clone https://github.com/barais/ESIRTPDockerSampleApp \
    && cd ESIRTPDockerSampleApp 

############################################
# Building opencv jar
RUN git clone https://github.com/opencv/opencv.git \
    && cd opencv \
    && git checkout -b 3.4 origin/3.4 \ 
    && mkdir build \
    && cd build \
    && cmake -D BUILD_SHARED_LIBS=OFF .. \
    && make -j8 

#############################################
#Excuting the application
RUN mvn install:install-file "-Dfile=./opencv/build/bin/opencv-346.jar" "-DgroupId=org.opencv" "-DartifactId=opencv" "-Dversion=3.4.6" "-Dpackaging=jar"
RUN cd ..

VOLUME /tmp

# The application's jar file
ARG JAR_FILE=target/target/fatjar-0.0.1-SNAPSHOT.jar

# Add the application's jar to the container
#ADD ${JAR_FILE} fatjar.jar

# Run the jar file 
ENTRYPOINT ["java","-Djava.library.path=./opencv/build/lib/","-jar","/fatjar.jar"]

############################################
EXPOSE 8080

############################################
CMD ["/bin/bash"]