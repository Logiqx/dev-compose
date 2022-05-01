ARG NOTEBOOK_VERSION
FROM jupyter/base-notebook:${NOTEBOOK_VERSION:-latest}

# Ideally apt-get would use sudo but it requires the jovyan password
USER root

# Check for latest packages
RUN apt-get update

# Do a full installation of gcc including recommended packages
RUN apt-get install -y gcc

# Intentionally exclude the typical cleanup of "rm -rf /var/lib/apt/lists/*"
RUN apt-get install -y --no-install-recommends mysql-client

# Switch back to the normal user
USER jovyan

# Microsoft Excel - covid-stats, scw-comp and wsw-results
# Note that xlrd 1.2.* is required for .xlsx support (dropped in xlrd 2.0.0)
RUN pip install --no-cache-dir \
    xlrd==1.2.*

# SQL - wca-ipy and wca-ipy-private
RUN pip install --no-cache-dir \
    PyMySQL==1.0.* \
    sqlparse==0.4.*

# Fuzzy matching - wsw-results
RUN pip install --no-cache-dir \
    Levenshtein==0.16.* \
    pyphonetics==0.5.*

# HTTP / API - covid-stats and twitter
RUN pip install --no-cache-dir \
    google==3.0.* \
    requests==2.26.* \
    tweepy==4.4.*

# HTML parsing and generation - many projects
RUN pip install --no-cache-dir \
    beautifulsoup4==4.10.* \
    Jinja2==3.0.* \
    lxml==4.7.*

# Scientific - covid-stats and wsw-results
RUN pip install --no-cache-dir \
    matplotlib==3.5.* \
    numpy==1.21.* \
    scipy==1.7.*

# GPS + fitness trackers
RUN pip install --no-cache-dir \
    fitdecode==0.10.* \
    gpxpy==1.5.*
