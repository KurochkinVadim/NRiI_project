FROM python:3.9-alpine as builder
WORKDIR /app
COPY requirements.txt .
RUN apk add --no-cache gcc musl-dev python3-dev libffi-dev openssl-dev
RUN pip install --user --no-cache-dir -r requirements.txt
FROM python:3.9-alpine
WORKDIR /app
COPY --from=builder /root/.local/lib/python3.9/site-packages /root/.local/lib/python3.9/site-packages
ENV PYTHONPATH=/root/.local/lib/python3.9/site-packages
COPY app.py .
CMD ["python", "app.py"]
