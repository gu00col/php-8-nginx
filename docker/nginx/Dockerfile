FROM nginx:latest

# Copiar o arquivo de configuração do Nginx
COPY ./docker/nginx/default.conf /etc/nginx/conf.d/default.conf

# Criar o diretório snippets e adicionar o arquivo fastcgi-php.conf
RUN mkdir -p /etc/nginx/snippets && \
    echo 'fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;' > /etc/nginx/snippets/fastcgi-php.conf
