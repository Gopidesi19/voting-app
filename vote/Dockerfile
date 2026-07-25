FROM python:3.11-slim AS builder

WORKDIR /app

COPY requirements.txt .

RUN pip install --prefix=/install --no-cache-dir -r requirements.txt

COPY . .

FROM python:3.11-slim 

WORKDIR /app

COPY --from=builder /install /usr/local

COPY --from=builder app/ .

#RUN  addgroup -S appgroup && adduser -S appuser -G appgroup

#RUN chown -R appuser:appgroup /app

#USER appuser

EXPOSE 80

CMD ["python","app.py"]
