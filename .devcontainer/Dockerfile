# # Use the mcr.microsoft.com/devcontainers/python:0-3.11 image as the base image
# FROM mcr.microsoft.com/devcontainers/python:0-3.11

# Set the user argument and default value
ARG user=vscode
ARG venv_path=/home/$user/venv

# Set the user and home directory
USER $user
ENV HOME /home/$user

# Disable pip version check and set cache directory to /tmp/pip-cache
ENV PIP_DISABLE_PIP_VERSION_CHECK 1
ENV PIP_NO_CACHE_DIR off
ENV PIP_CACHE_DIR /tmp/pip-cache

# Run apt-get update to update package lists
RUN sudo apt-get update

# Create a virtual environment in the home directory
RUN python3 -m venv $venv_path

# Set the environment variables to activate the virtual environment
ENV VIRTUAL_ENV $venv_path
ENV PATH $VIRTUAL_ENV/bin:$PATH

# Copy the requirements.txt file to the container
COPY requirements.txt /tmp/requirements.txt

# Activate the virtual environment and install the Python dependencies from requirements.txt
RUN /bin/bash -c "source $VIRTUAL_ENV/bin/activate && pip install --no-cache-dir -r /tmp/requirements.txt"

# Remove the temporary requirements.txt file
RUN rm /tmp/requirements.txt
