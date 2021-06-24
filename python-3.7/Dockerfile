ARG BUILD_VERSION=3.7
FROM python:${BUILD_VERSION}-slim
ENV TZ=Asia/Shanghai LANG=en_US.utf8 LC_LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8
RUN sed -i -e "s/\/\/archive\.ubuntu/\/\/mirrors.aliyun/" /etc/apt/sources.list \
    && apt-get update \
    && apt-get install -y --no-install-recommends tzdata \
    && echo "Asia/Shanghai" > /etc/timezone \
    && dpkg-reconfigure --frontend noninteractive tzdata
