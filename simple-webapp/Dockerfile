FROM nginx:stable-alpine

# Copy what we've installed/built from production
COPY ./config/nginx-default.conf /etc/nginx/templates/default.conf.template
COPY --chmod=755 ./config/15-default.envsh /docker-entrypoint.d/

RUN mkdir -p /var/www/html/
COPY src/ /var/www/html

RUN mkdir -p /var/cache/nginx /var/run /var/www/html \
 && chown -R 101:101 /var/cache/nginx /var/run /etc/nginx/conf.d \
 && chown 101:101 /run

USER 101
EXPOSE 8080
