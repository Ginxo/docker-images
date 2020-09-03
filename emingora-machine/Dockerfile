FROM fedora:32

#Install Open JDK 8

RUN dnf update -y \
&& dnf -y install curl tar

RUN curl -L -b "oraclelicense=a" -o jdk-8-linux-x64.tar.gz -O https://javadl.oracle.com/webapps/download/AutoDL?BundleId=239835_230deb18db3e4014bb8e3e8324f81b43 \
&& mkdir -p /usr/lib/jvm/java-8 \
&& tar -zxf jdk-8-linux-x64.tar.gz -C /usr/lib/jvm/java-8

ENV JAVA_HOME /usr/lib/jvm/java-8/jdk1.8.0_221
ENV PATH $JAVA_HOME/bin:$PATH

# Install Maven
RUN dnf -y install git openssl bash procps gnupg
ARG MAVEN_VERSION=3.6.3
ARG BASE_URL=https://apache.osuosl.org/maven/maven-3/${MAVEN_VERSION}/binaries
ARG SHA=c35a1803a6e70a126e80b2b3ae33eed961f83ed74d18fcd16909b2d44d7dada3203f1ffe726c17ef8dcca2dcaa9fca676987befeadc9b9f759967a8cb77181c0
RUN echo "Installing Maven"
RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && echo "Downloading maven" \
  && curl -fsSL -o /tmp/apache-maven.tar.gz ${BASE_URL}/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
  \
  && echo "Checking download hash" \
  && echo "${SHA}  /tmp/apache-maven.tar.gz" | sha512sum -c - \
  \
  && echo "Unziping maven" \
  && tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1 \
  \
  && echo "Cleaning and setting links" \
  && rm -f /tmp/apache-maven.tar.gz \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven \
  && MAVEN_CONFIG "$USER_HOME_DIR/.m2" \
  && PATH $MAVEN_HOME/bin:$PATH
