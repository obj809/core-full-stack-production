# flask-backend/Dockerfile

FROM python:3.11-slim AS base

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app

# Add wget so the compose healthcheck (which uses wget) works
RUN apt-get update && apt-get install -y --no-install-recommends \
      build-essential default-libmysqlclient-dev wget \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt \
    && pip install --no-cache-dir gunicorn

COPY . .

# Run as non-root
RUN useradd -m -u 10001 appuser
USER appuser

EXPOSE 5000

# Gunicorn server
CMD ["gunicorn", "-w", "3", "-k", "gthread", "--threads", "4", "--timeout", "60", \
     "-b", "0.0.0.0:5000", "app:app"]
