# ИНСТРУКЦИЯ ПО ЗАПУСКУ
------------------------

Dockerfile

```bash

# Используем официальный образ Node.js (рекомендуется LTS версия)
#FROM node:18-alpine

# Устанавливаем Gemini CLI глобально в контейнере
#RUN npm install -g @google/gemini-cli

# Создаём рабочую директорию внутри контейнера
#WORKDIR /app

# Устанавливаем точку входа по умолчанию (чтобы просто получить bash-шелл при запуске)
#CMD ["bash"]

# Используем официальный образ Node.js (рекомендуется LTS версия)
#FROM node:18-alpine

# Устанавливаем bash (Alpine Linux использует sh по умолчанию)
#RUN apk add --no-cache bash

# Устанавливаем Gemini CLI глобально в контейнере
#RUN npm install -g @google/gemini-cli

# Создаём рабочую директорию внутри контейнера
#WORKDIR /app

# Устанавливаем bash как ENTRYPOINT
#ENTRYPOINT ["/bin/bash"]
#CMD []

# Use official Node.js LTS version with File API support
FROM node:22-alpine

# Install bash (Alpine uses sh by default)
RUN apk add --no-cache bash

# Install Gemini CLI globally
RUN npm install -g @google/gemini-cli

# Set working directory
WORKDIR /app

# Use bash as ENTRYPOINT
ENTRYPOINT ["/bin/bash"]

```
**Для работы нужен GEMINI-API-KEY**

Закройте все активные контейнеры (если есть).

Откройте PowerShell.

Перейдите в директорию, которую вы хотите смонтировать:

```PowerShell

cd J:\Video\

```
Запустите Docker команду, используя ${PWD}:``

```PowerShell

docker run -it --rm -v "${PWD}:/app" -e GEMINI_API_KEY="API-KEY" gemini-cli-env

```
### После запуска, внутри контейнера снова сделайте ls -la /app. Здесь вы должны увидеть свои файлы.