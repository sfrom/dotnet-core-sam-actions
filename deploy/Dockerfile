# FROM microsoft/dotnet:2.1.500-sdk

# LABEL "com.github.actions.name"="dotnet lambda deploy"
# LABEL "com.github.actions.description"="Run dotnet lambda deploy"
# LABEL "com.github.actions.icon"="play-circle"
# LABEL "com.github.actions.color"="purple"

# LABEL "repository"="https://github.com/evalytica/dotnet-lambda-actions"
# LABEL "homepage"="https://github.com/evalytica/dotnet-lambda-actions"
# LABEL "maintainer"="Evalytica DevOps Team <evalytica@veradigmhealth.com>"

# RUN apt-get update && \
#     apt-get install -y --no-install-recommends \
#       groff \
#       jq \
#       python \
#       python3-pip \
#       python3-setuptools \
#       zip \
#     && apt-get install -y software-properties-common \
#     && add-apt-repository ppa:deadsnakes/ppa \
#     && apt-get update \
#     && apt-get install python3.7 \
#     && rm -rf /var/lib/apt/lists/* \
#     && pip3 install awscli \
#     && pip3 install aws-sam-cli

FROM buildpack-deps:bionic-scm

# Install .NET CLI dependencies
# RUN apt-get update \
#     && apt-get install -y --no-install-recommends \
#         libc6 \
#         libgcc1 \
#         libgssapi-krb5-2 \
#         libicu60 \
#         liblttng-ust0 \
#         libssl1.0.0 \
#         libstdc++6 \
#         zlib1g \
#     && rm -rf /var/lib/apt/lists/*

# Install .NET Core SDK
# ENV DOTNET_SDK_VERSION 2.1.802

# RUN curl -SL --output dotnet.tar.gz https://dotnetcli.blob.core.windows.net/dotnet/Sdk/$DOTNET_SDK_VERSION/dotnet-sdk-$DOTNET_SDK_VERSION-linux-x64.tar.gz \
#     && dotnet_sha512='8601ec68fa8978c5a08a696cc69f5e0aa9dabf274bade40e2fd9ded2e563f2cc7a1cb418a95c9b52e1fa9b6c4a30993be68cb3b6bbda4598c57b37ec9ce992ad' \
#     && echo "$dotnet_sha512 dotnet.tar.gz" | sha512sum -c - \
#     && mkdir -p /usr/share/dotnet \
#     && tar -zxf dotnet.tar.gz -C /usr/share/dotnet \
#     && rm dotnet.tar.gz \
#     && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet

# Trigger first run experience by running arbitrary cmd to populate local package cache
RUN dotnet help

# Trigger first run experience by running arbitrary cmd to populate local package cache
RUN dotnet help

RUN dotnet tool install -g Amazon.Lambda.Tools

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
