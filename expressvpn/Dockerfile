
# Run expressvpn in a container

FROM debian:11-slim

ENV ACTIVATION_CODE Code
ENV LOCATION smart
ENV PREFERRED_PROTOCOL auto
ENV LIGHTWAY_CIPHER auto

# ARG APP=expressvpn_3.34.1.0-1_amd64.deb
ARG APPv=xv_3.38.0.3-1_amd64.deb

RUN apt-get update && apt-get install -y --no-install-recommends \
    libterm-readkey-perl ca-certificates wget expect iproute2 iputils-ping curl procps libnm0 iptables dnsutils\
    && rm -rf /var/lib/apt/lists/* \
    && wget -q "https://www.download-express-apps.net/clients/linux/${APPv}" -O /tmp/${APPv} \
  # && wget -q "https://www.expressvpn.works/clients/linux/${APP}" -O /tmp/${APP} \
    && dpkg -i /tmp/${APPv} \
    && rm -rf /tmp/*.deb
  # && apt-get purge -y --auto-remove wget

COPY entrypoint.sh /tmp/entrypoint.sh
COPY expressvpnActivate.sh /tmp/expressvpnActivate.sh

ENTRYPOINT ["/bin/bash", "/tmp/entrypoint.sh"]
