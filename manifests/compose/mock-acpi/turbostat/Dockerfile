FROM quay.io/centos/centos:stream9-minimal@sha256:8fbcc4e99328e3cb9ec2d52eaeb1d53bedfd5c504d4d84fbd0513481281efd0e
RUN microdnf -y install kernel-tools
RUN microdnf install -y python3 python3-pip
RUN pip install prometheus_client
WORKDIR /app
COPY ./run_turbostat.py .
USER 0
CMD ["python3", "/app/run_turbostat.py"]

