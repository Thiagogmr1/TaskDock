# Imagem base Node.js
FROM node:18

# Definir o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copia os arquivos de dependência e instala
COPY package*.json ./
RUN npm install

# Copia o restante dos arquivos da aplicação
COPY . .

# Expõe a porta onde o backend irá rodar
EXPOSE 3001

# Comando para iniciar a aplicação
CMD ["npm", "start"]