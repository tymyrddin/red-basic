# SilentTrinity container for Windows targets

file: ~/SILENTTRINITY/Dockerfile:

```text
# The base Docker image containing binaries to run Python 3.7
FROM python:stretch-slim-3.7

# Install git, make, and gcc tools
RUN apt-get update && apt-get install -y git make gcc

# Download SILENTTRINITY and change directories
RUN git clone https://github.com/byt3bl33d3r/SILENTTRINITY/ /root/st/
WORKDIR /root/st/

# Install the Python requirements
RUN python3 -m pip install -r requirements.txt

# Inform future Docker users that they need to bind port 5000
EXPOSE 5000

# ENTRYPOINT is the first command the container runs when it starts
ENTRYPOINT ["python3", "teamserver.py", "0.0.0.0", "stringpassword"]
```

Build with:

    # docker build -t silent .