# Use the official Ubuntu base image
FROM ubuntu:22.04

# Set environment variables to avoid interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Update and install required dependencies
RUN apt-get update && apt-get install -y \
    curl \
    build-essential \
    clang \
    lldb \
    llvm \
    libssl-dev \
    pkg-config \
    git \
    && rm -rf /var/lib/apt/lists/*

# Add Rust to PATH
# Verify installations
ENV PATH="/root/.cargo/bin:${PATH}"

# Install Rust using rustup
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs  >/root/rustup-init.sh && \
    chmod +x /root/rustup-init.sh && \
    /root/rustup-init.sh -y --default-toolchain stable && \
    rm /root/rustup-init.sh || exit 1
# Set default working directory
WORKDIR /workspace

# Default command
CMD ["/bin/bash"]