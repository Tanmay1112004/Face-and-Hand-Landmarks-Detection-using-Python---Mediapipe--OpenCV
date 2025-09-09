# Use Microsoft's devcontainer python image with Python 3.11
FROM mcr.microsoft.com/vscode/devcontainers/python:0-3.11

ENV DEBIAN_FRONTEND=noninteractive

# Install system deps (libGL fix + ffmpeg for video handling)
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        libgl1 libglib2.0-0 libsm6 libxext6 libxrender1 ffmpeg && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /workspace

# Copy requirements (the devcontainer build context is repo root)
COPY requirements.txt /workspace/requirements.txt

# Install pip deps
RUN pip install --upgrade pip && pip install --no-cache-dir -r /workspace/requirements.txt

# expose streamlit port
EXPOSE 8501

CMD [ "bash" ]
