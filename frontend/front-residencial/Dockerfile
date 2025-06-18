# Etapa 1: Construção da aplicação
FROM node:18-alpine3.18 AS builder

WORKDIR /app

# Copie apenas os arquivos necessários para instalar dependências e aproveitar cache
COPY package.json package-lock.json ./

# Instala dependências de produção
RUN npm ci

# Copie o restante do código
COPY . .

# Build da aplicação
RUN npm run build

# Etapa 2: Servindo a aplicação
FROM nginx:1.25-alpine

# Remove configuração padrão do Nginx
RUN rm -f /etc/nginx/conf.d/default.conf

# Copia configuração personalizada
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copia o build gerado para o diretório padrão do Nginx
COPY --from=builder /app/dist/site-apartamento/browser /usr/share/nginx/html/

# Exponha a porta padrão
EXPOSE 80

# Inicia o Nginx
CMD ["nginx", "-g", "daemon off;"]
