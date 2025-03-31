FROM python:3.9

WORKDIR /app

COPY requirements.txt .
RUN pip install gunicorn==20.1.0
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

ENV PYTHONUNBUFFERED=1

CMD python manage.py collectstatic --noinput --clear && \
    python manage.py migrate && \
    gunicorn kittygram_backend.wsgi:application --bind 0.0.0.0:9000
