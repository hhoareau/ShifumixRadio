FROM siomiz/chrome

MAINTAINER Hoareau hhoareau@gmail.com

RUN apt-get install --no-install-recommends --no-install-suggests -y \
                vlc \
        && rm -rf /var/lib/apt/lists/* \
        && sed -i 's/geteuid/getppid/' /usr/bin/vlc

RUN echo "load-module module-native-protocol-unix" >> "/etc/pulse/default.pa"
RUN echo "load-module module-suspend-on-idle timeout=1" >> "/etc/pulse/default.pa"
RUN echo "load-module module-null-sink sink_name=rtp" >> "/etc/pulse/default.pa"
RUN echo "load-module module-rtp-send source=rtp.monitor rate=48000 channels=2 format=s16be" >> "/etc/pulse/default.pa"

#RUN apt-get install pactl
#RUN pactl load-module module-rtp-send source=alsa_output.0.analog-stereo.monitor destination=127.0.0.1 port=8080 loop=1

CMD ["google-chrome", "shifumix.com"]