FROM python:3.11-slim

# Установка зависомостей
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*


# Установка рабочего каталога
WORKDIR /app

# Копируем зависимости
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Копируем всё приложение
COPY . .

# Команда по умолчанию
CMD ["gunicorn", "todo_project.wsgi:application", "--bind", "0.0.0.0:8000"]