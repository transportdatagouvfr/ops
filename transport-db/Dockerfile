# docker build -t test:postgres . --platform linux/amd64
FROM postgis/postgis:14-3.5

RUN apt-get update
RUN apt-get install -y lsb-release wget

# Adapted from https://docs.tigerdata.com/self-hosted/latest/install/installation-linux/#install-and-configure-timescaledb-on-postgresql
RUN echo "deb https://packagecloud.io/timescale/timescaledb/debian/ $(lsb_release -c -s) main" | tee /etc/apt/sources.list.d/timescaledb.list
RUN wget --quiet -O - https://packagecloud.io/timescale/timescaledb/gpgkey | gpg --dearmor -o /etc/apt/trusted.gpg.d/timescaledb.gpg
RUN apt-get update

# https://packagecloud.io/timescale/timescaledb
RUN apt-get install -y timescaledb-2-postgresql-14='2.17.2*' timescaledb-2-loader-postgresql-14='2.17.2*'
# Err: could not find postgresql.conf at any of these locations:
# RUN timescaledb-tune