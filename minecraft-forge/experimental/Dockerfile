FROM ubuntu:22.04
LABEL maintainer="mwitek"
WORKDIR /minecraft/forge/server
ENV jdkVersion="openjdk-17-jre"
RUN apt-get update
RUN apt-get install -y ${jdkVersion}
RUN apt-get install -y wget
ENV forgeInstallerVersion="1.18.2-40.1.51"
ARG installerUrl="https://maven.minecraftforge.net/net/minecraftforge/forge/${forgeInstallerVersion}/forge-${forgeInstallerVersion}-installer.jar"
ARG installerName="forge-${forgeInstallerVersion}-installer.jar"
# download forge
RUN wget ${installerUrl}
# run forge server
RUN java -jar ${installerName} --installServer
# cleanup
RUN rm ${installerName}
# accepting EULA
RUN echo eula=true > eula.txt
# copying server.properties
COPY server.properties /minecraft/forge/server/
# configuring
RUN mkdir mods
# Setting up memory limits
ENV serverMemoryLimit=4G
RUN echo "\n-Xmx${serverMemoryLimit}" > user_jvm_args.txt
EXPOSE 25565/udp
CMD ["bash", "./run.sh"]