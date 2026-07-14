# You can pick any Debian/Ubuntu-based image. 😊
FROM ubuntu:26.04

RUN apt update && apt install -y \
    gnupg \
    curl \
    wget  \
    software-properties-common

RUN wget -O- https://apt.releases.hashicorp.com/gpg | \
    gpg --dearmor | \
    tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null && \
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
    https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
    tee /etc/apt/sources.list.d/hashicorp.list

# Install Terraform
RUN apt update && apt install -y \
    terraform \
    direnv \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/cloudflare/cf-terraforming/releases/download/v0.27.0/cf-terraforming_0.27.0_linux_amd64.tar.gz &&\
    tar -xzf cf-terraforming_0.27.0_linux_amd64.tar.gz && \
    mv cf-terraforming /usr/local/bin/cf-terraforming && \
    rm cf-terraforming_0.27.0_linux_amd64.tar.gz && \
    chmod +x /usr/local/bin/cf-terraforming

# Set up direnv hook
RUN echo 'eval "$(direnv hook bash)"' >> ~/.bashrc && \
    echo 'eval "$(direnv hook bash)"' >> ~/.bash_profile && \
    cf-terraforming completion bash > /etc/bash_completion.d/cf-terraforming && \
    terraform -install-autocomplete
