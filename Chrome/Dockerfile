#HowTO use

#Reference: https://medium.com/dot-debug/running-chrome-in-a-docker-container-a55e7f4da4a8

#Create Image
 #docker build -t local/chrome:0.0.1 .

#Use Image
#docker run -p 5900:5900 -e VNC_SERVER_PASSWORD=password --user apps --privileged local/chrome:0.0.1 bash -c 'sh bootstrap.sh'


FROM ubuntu:trusty

RUN apt-get update; apt-get clean

# Add a user for running applications.
RUN useradd apps
RUN mkdir -p /home/apps && chown apps:apps /home/apps

#Qual usuario logado
#USER apps

# Install x11vnc.
RUN apt-get install -y x11vnc

# Install xvfb.
RUN apt-get install -y xvfb

# Install fluxbox.
RUN apt-get install -y fluxbox

# Install wget.
RUN apt-get install -y wget

# Install wmctrl.
RUN apt-get install -y wmctrl

# Set the Chrome repo.
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list

# Install Chrome.
RUN apt-get update && apt-get -y install google-chrome-stable

COPY bootstrap.sh /

#CMD 'bash sh bootstrap.sh'