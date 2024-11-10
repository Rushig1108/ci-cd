# Start from the official Python image
FROM python:3.8

# Install Docker CLI and other dependencies
RUN apt-get update && \
    apt-get install -y \
    docker.io \
    git \
    unzip \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Install Sonar Scanner
RUN curl -sSLo sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.6.2.2472-linux.zip && \
    unzip sonar-scanner.zip -d /opt && \
    rm sonar-scanner.zip

# Set environment variables for Sonar Scanner
ENV SONAR_SCANNER_HOME=/opt/sonar-scanner-4.6.2.2472-linux
ENV PATH="${SONAR_SCANNER_HOME}/bin:${PATH}"

# Set a default working directory
WORKDIR /workspace

# Install Python dependencies
COPY requirements.txt /workspace/
RUN pip install --no-cache-dir -r requirements.txt

# Set the default command (optional)
CMD ["bash"]
