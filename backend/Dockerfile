FROM python:3.12

WORKDIR /app

# Устанавливаем необходимые системные пакеты
RUN apt-get update && apt-get install -y \
    build-essential \
    && rm -rf /var/lib/apt/lists/*


RUN pip install gunicorn==23.0.0 

COPY requirements.txt .

# Устанавливаем setuptools который включает distutils
RUN pip install setuptools wheel --no-cache-dir
RUN pip install -r requirements.txt --no-cache-dir

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]