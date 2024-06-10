FROM quay.io/soliek_yao/ireconcile-python-slim:latest@sha256:d363b04d364e9ac69b23f70da67ad5fa81fa562776525b85fe63f33992dbee4e

WORKDIR /app
USER 0

# Install dependencies
RUN pip install prometheus_client

# Copy the Python script into the container
COPY mock-acpi.py .

# Run the Python script
CMD ["mock-acpi.py"]
