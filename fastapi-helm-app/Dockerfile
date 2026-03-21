FROM python:3.10-slim

WORKDIR /app

COPY app/ ./app

RUN pip install -r app/requirements.txt

CMD ["uvicorn", "app.app:app", "--host", "0.0.0.0", "--port", "8000"]