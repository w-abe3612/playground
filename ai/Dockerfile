FROM python:3.12-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    git curl \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace
RUN pip install --no-cache-dir jupyterlab numpy pandas matplotlib

EXPOSE 8888
CMD ["bash", "-lc", "jupyter lab --ip=0.0.0.0 --no-browser --NotebookApp.token="]