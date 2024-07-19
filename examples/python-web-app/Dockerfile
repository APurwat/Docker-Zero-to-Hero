# Use an official Ubuntu runtime as a parent image
FROM ubuntu:latest

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file first for leveraging Docker cache
COPY requirements.txt /app

# Install dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    pip3 install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY devops /app/devops

# Set the working directory to where the manage.py is located, if it's in /app/devops
WORKDIR /app/devops

# Set the default command to run the application
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
