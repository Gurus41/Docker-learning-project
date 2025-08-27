# Use Ubuntu as base image
FROM ubuntu:latest

# Set working directory
WORKDIR /app

# Copy project files
COPY requirements.txt /app/
COPY devops /app/

# Install Python, curl, jq, unzip, ngrok (v3)
RUN apt-get update && apt-get install -y \
    python3 python3-pip python3-venv curl unzip jq gnupg apt-transport-https ca-certificates \
    && curl -s https://ngrok-agent.s3.amazonaws.com/ngrok.asc | tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
    && echo "deb https://ngrok-agent.s3.amazonaws.com buster main" | tee /etc/apt/sources.list.d/ngrok.list \
    && apt-get update && apt-get install -y ngrok \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
RUN pip3 install --no-cache-dir --break-system-packages -r requirements.txt

# Expose Django & ngrok ports
EXPOSE 8000 4040

# Set ngrok authtoken (can be overridden at runtime with -e)
ENV NGROK_AUTHTOKEN=YOUR_AUTHTOKEN_HERE

# Start Django + ngrok together
CMD sh -c "python3 manage.py runserver 0.0.0.0:8000 & \
    ngrok config add-authtoken $NGROK_AUTHTOKEN && \
    ngrok http 8000 --log=stdout"

###### Commands to build the image ######

# docker build -t gurus41/django-ngrok-app . 

# 👉 The container will:
# -t gurus41/python-web-app:ubuntu → names & tags the image 
# . → means build from the current directory 

###### Commands to run the container ######

# docker run -p 8000:8000 -p 4040:4040 -e NGROK_AUTHTOKEN=<your-token> gurus41/django-ngrok-app

# 👉 The container will:
#Start your Django app on http://localhost:8000
#Start ngrok to tunnel port 8000.
#Query the ngrok API (http://127.0.0.1:4040/api/tunnels).
#Print out only the public ngrok URL (like https://xyz.ngrok-free.app).#

###### Push to Docker Hub #####

# docker push gurus41/django-ngrok-app:latest 

# docker push → uploads an image from your local machine to Docker Hub (or another registry).
# gurus41 → your Docker Hub username (namespace).
# django-ngrok-app → the repository name on Docker Hub.
# :latest → the image tag you are pushing (default tag if none is given).

###### Verify the push ######

# docker pull gurus41/django-ngrok-app:latest 

# docker pull → downloads an image from Docker Hub (or any registry) to your local system.
# gurus41 → Docker Hub username (the namespace where the repo lives).
# django-ngrok-app → the repository name.
# :latest → the tag (in this case, latest version of the image).