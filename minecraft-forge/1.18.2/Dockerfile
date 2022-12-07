FROM ubuntu:22.04
LABEL maintainer="mwitek"
WORKDIR /minecraft/forge/server
RUN apt-get update
RUN apt-get install -y openjdk-17-jre
RUN apt-get install -y wget
ENV forgeInstallerUrl="https://maven.minecraftforge.net/net/minecraftforge/forge/1.18.2-40.1.51/forge-1.18.2-40.1.51-installer.jar"
ENV forgeInstaller="forge-1.18.2-40.1.51-installer.jar"
# download forge
RUN wget ${forgeInstallerUrl}
# run forge server
RUN java -jar ${forgeInstaller} --installServer
# cleanup
RUN rm ${forgeInstaller}
# accepting EULA
RUN echo eula=true >eula.txt
# copying server.properties
COPY server.properties /minecraft/forge/server/
# configuring
RUN mkdir mods
# Setting up memory limits
ENV serverMemoryLimit=4G
RUN echo "\n-Xmx${serverMemoryLimit}" > user_jvm_args.txt
EXPOSE 25565/udp
CMD ["bash", "./run.sh"]