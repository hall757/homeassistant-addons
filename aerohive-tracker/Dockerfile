FROM ghcr.io/home-assistant/aarch64-base:latest
ENTRYPOINT 
CMD python3 /usr/bin/aerohive_tracker
RUN curl -sSLf -o /usr/bin/tempio \
      "https://github.com/home-assistant/tempio/releases/download/2021.09.0/tempio_aarch64" && \
    apk add gcc py3-pynacl py3-cryptography py3-paho-mqtt \
      py3-cryptography py3-scp py3-yaml py3-pip py3-pynacl \
      py3-pyserial py3-cffi py3-future py3-tz  && \
    pip3 install aeromiko --break-system-packages
# install the app
COPY aerohive_tracker /usr/bin/aerohive_tracker
