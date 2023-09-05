ARG BUILD_FROM TEMPIO_VERSION BUILD_ARCH
FROM $BUILD_FROM
ENTRYPOINT 
CMD python3 /usr/bin/aerohive_tracker
RUN curl -sSLf -o /usr/bin/tempio "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}" ; \
    apk add gcc py3-pynacl py3-cryptography py3-paho-mqtt py3-cryptography py3-scp py3-yaml py3-pip py3-pynacl py3-pyserial ; \
    pip3 install aeromiko 2> /dev/null
# install the app
COPY aerohive_tracker /usr/bin/aerohive_tracker
