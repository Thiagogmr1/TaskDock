# Etapa 1: Build do frontend
FROM node:18 AS build

# Definir o diretório de trabalho dentro do contêiner
WORKDIR /app

#Copia apenas os arquivos de dependências para aproveitar cache do Docker
COPY package*.json ./

# Instalar dependências do projeto
RUN npm install

# Copiar o restante dos arquivos do projeto
COPY . .

# Executa o build de produção (gera a pasta 'dist' no caso do Vite)
RUN npm run build

#=================Etapa 2: Servir com Nginx=================

# Usar uma imagem leve do Nginx, leve e otimizada para produção
FROM nginx:alpine

# Copiar os arquivos construídos da etapa anterior para o diretório padrão do Nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Expor a porta 80 para acesso ao servidor web
EXPOSE 80

# Comando para iniciar o Nginx em primeiro plano
CMD ["nginx", "-g", "daemon off;"]
