# FROM python:3.10-alpine
# WORKDIR /app
# COPY requirements.txt .
# RUN pip install --upgrade pip
# RUN pip install thriftpy2==0.4.16
# RUN pip install --no-cache-dir -r requirements.txt
# COPY . .
# Use an official Python runtime as a parent image
FROM python:3.5-slim

# Set the working directory in the container
WORKDIR /app

# Install system dependencies (gcc and other build tools)
RUN apt-get update && \
    apt-get install -y --no-install-recommends gcc python3-dev && \
    rm -rf /var/lib/apt/lists/*

# Copy the requirements file
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .
CMD ["python","main.py"]
