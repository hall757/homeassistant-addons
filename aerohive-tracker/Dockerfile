# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM
# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

# Install requirements
RUN apk add gcc py3-pynacl py3-cryptography py3-paho-mqtt py3-cryptography py3-scp py3-yaml py3-pip py3-pynacl py3-pyserial
RUN pip3 install aeromiko 2> /dev/null
# Clear entrypoint
ENTRYPOINT 
# Set startup command
CMD python3 /usr/bin/aerohive_tracker
# install the app
COPY aerohive_tracker /usr/bin/aerohive_tracker
