# 1. Базовый образ
FROM node:20-alpine

# 2. Рабочая директория
WORKDIR /app

COPY package*.json ./
RUN npm install

# 4. Копируем весь проект
COPY . .

# 5. Генерируем Prisma Client
RUN npm install prisma -g prisma

RUN prisma generate

# Копируем Prisma schema и URL базы данных в контейнер
COPY prisma/schema.prisma ./prisma/

# 7. Открываем порт (если нужно)
EXPOSE 3000

# 8. Команда запуска
CMD ["npm", "run", "start"]