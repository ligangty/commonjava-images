# Change base image to use ubi8
FROM registry.access.redhat.com/ubi8/openjdk-11:1.20

LABEL Name="nos-java-base" \
    Version="8" \
    Release="2" \
    maintainer="RedHat SPMM Team <nos-devel@redhat.com>"

USER root

ENV TZ UTC

ADD RH-IT-Root-CA.crt /etc/pki/ca-trust/source/anchors/RH-IT-Root-CA.crt
ADD 2022-IT-Root-CA.pem /etc/pki/ca-trust/source/anchors/2022-IT-Root-CA.pem
RUN update-ca-trust extract

RUN microdnf -y update && \
    microdnf -y install wget tar which curl && \
    microdnf clean all && \
    rm -rf /var/cache/yum

ENTRYPOINT ["/bin/sh"]
