FROM ubuntu:latest

RUN apt update && apt install -y pcmanfm featherpad wget

#Installation Rider
RUN mkdir rider
RUN cd /rider
RUN wget https://download.jetbrains.com/rider/JetBrains.Rider-2022.2.2.tar.gz -O rider-install.tar.gz
RUN tar -xvf rider-install.tar.gz && rm rider-install.tar.gz

#SDK Mono
RUN apt install -y mono-complete

#SDK .Net6
RUN wget https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN rm packages-microsoft-prod.deb
RUN apt-get update
RUN apt-get install -y dotnet-sdk-6.0

#Installation Git
RUN apt-get -y install git

#Installation Navigateur Chrome
RUN sh -c 'echo "deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google-chrome.list'
RUN wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O linux_signing_key.pub
RUN apt-key add linux_signing_key.pub
RUN apt update
RUN apt --fix-broken install -y
RUN apt-get install -y google-chrome-stable

#Configuration Chrome dans docker
RUN wget https://raw.githubusercontent.com/jfrazelle/dotfiles/master/etc/docker/seccomp/chrome.json -O ~/chrome.json 

ENV DISPLAY=host.docker.internal:0.0

RUN useradd -ms /bin/bash rider

USER rider

CMD pcmanfm
