FROM public.ecr.aws/bitnami/python:3.8.7-prod

LABEL maintainer=opomer@amazon.co.uk

WORKDIR /app
ADD requirements.txt /app/requirements.txt 

RUN apt-get update && \
    apt-get install --no-install-recommends curl -y && \
    rm -rf /var/lib/apt/lists/* && \
    pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt 

COPY ./myweb /app/

EXPOSE 80

HEALTHCHECK --interval=30s --timeout=5s \
  CMD curl -sf http://localhost/health || exit 1

ENTRYPOINT ["python"]
CMD ["app.py"]
