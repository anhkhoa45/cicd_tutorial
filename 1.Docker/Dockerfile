FROM python:3.7

# Set the working directory (workdir) to /app
RUN mkdir /app
WORKDIR /app

# Install dependencies
RUN apt update && apt install -y redis-server

# Set application environment variables
ENV FLASK_APP=main.py
ENV FLASK_RUN_HOST=0.0.0.0

# Set application environment variables
COPY app/requirements.txt .
RUN pip install -r requirements.txt

# Expose port 5000 and 6379
EXPOSE 5000
EXPOSE 6379

# Copy the app files to workdir
COPY app .

# Default command when start a container
CMD ["bash", "-c", "redis-server --daemonize yes & flask run"]
