ARG BUILD_FROM
FROM $BUILD_FROM

# Setup base
RUN apk add --no-cache nginx openssl

# Copy data from rootfs to /
COPY rootfs /

WORKDIR /

# Tutorial
# Copy data for add-on
#COPY run.sh /
#RUN chmod a+x /run.sh
#CMD [ "/run.sh" ]