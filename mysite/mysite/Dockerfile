# Указываем базовый образ Python
FROM python:3.9-slim

# Устанавливаем рабочую директорию внутри контейнера
WORKDIR /app

# Копируем файл зависимостей
COPY requirements.txt /app/

# Устанавливаем зависимости
RUN pip install --no-cache-dir -r requirements.txt

# Копируем оставшиеся файлы проекта
COPY . /app/

# Выполняем миграции и подготавливаем статические файлы
RUN python manage.py migrate
RUN python manage.py collectstatic --noinput

# Указываем порт, который будет использоваться
EXPOSE 8000

# Устанавливаем команду для запуска приложения
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
