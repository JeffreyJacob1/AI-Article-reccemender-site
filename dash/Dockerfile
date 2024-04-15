# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at /usr/src/app
COPY . /usr/src/app

# Install any needed packages specified in requirements_app.txt
RUN pip install --no-cache-dir -r requirements_app.txt

# Create the data directory and set ownership
RUN mkdir -p /usr/src/app/data
RUN chown -R 1000:1000 /usr/src/app/data

# Create a non-root user and switch to it
RUN useradd -u 1000 appuser
USER appuser

# Make port 8050 available to the world outside this container
EXPOSE 8050

# Run the command to start the Dash app with Gunicorn
CMD ["gunicorn", "-b", "0.0.0.0:8050", "index:server"]