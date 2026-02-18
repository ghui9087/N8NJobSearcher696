FROM n8nio/runners:2.7.4 AS n8n-source

FROM python:3.13-bookworm

RUN apt-get update && apt-get install -y --no-install-recommends \
    ffmpeg \
    tini \
    && rm -rf /var/lib/apt/lists/*

COPY --from=n8n-source /usr/local/bin/task-runner-launcher /usr/local/bin/task-runner-launcher
COPY --from=n8n-source /opt/runners /opt/runners

COPY --from=ghcr.io/astral-sh/uv:latest /uv /usr/local/bin/uv

WORKDIR /opt/runners/task-runner-python
RUN uv venv --clear .venv

# Install Python dependencies using uv
RUN uv pip install --python .venv/bin/python \
    . \
    numpy \
    pandas \
    pydub \
    python-jobspy

COPY n8n-task-runners.json /etc/n8n-task-runners.json

RUN useradd -m runner && chown -R runner:runner /opt/runners
USER runner

ENTRYPOINT ["tini", "--", "task-runner-launcher"]
CMD ["javascript", "python"]
