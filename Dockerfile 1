FROM python:3.9-slim

RUN apt-get update && apt-get install -y --no-install-recommends

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY service/ ./service/

RUN useradd --uid 1000 theia && chown -R theia /app
USER theia

EXPOSE 8080
CMD ["gunicorn","--bind=0.0.0.0:8080","--log-level=info","service:app"]
