ARG PYTHON_DEP
WORKDIR /config
ENV PSACC_BASE_PATH=/ PSACC_PORT=5000 PSACC_OPTIONS=-c -r --web-conf PSACC_CONFIG_DIR=/config PYTHONPATH=/app
COPY /var/lib/apt /var/lib/apt # buildkit
COPY /var/cache/apt/ /var/cache/apt/ # buildkit
COPY /usr/local/lib /usr/local/lib # buildkit
COPY /usr/local/bin/ /usr/local/bin/ # buildkit
RUN |1 PYTHON_DEP=python3 python3-wheel python3-typing-extensions python3-pandas python3-six python3-dateutil python3-brotli python3-pycryptodome libatlas3-base python3-cryptography python3-scipy androguard python3-flask python3-paho-mqtt python3-ruamel.yaml ca-certificates python3-numpy /bin/sh -c apt-get install -y --no-install-recommends $PYTHON_DEP &&      apt-get clean ;      rm -rf /var/lib/apt/lists/* # buildkit
COPY /docker_files/init.sh /init.sh # buildkit
CMD ["/bin/sh" "-c" "/init.sh"]
