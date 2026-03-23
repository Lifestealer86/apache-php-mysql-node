FROM nginx:1.19.6-alpine
ARG FILE_CONFIG=nginx.conf

COPY $FILE_CONFIG /etc/nginx/conf.d/default.conf

# If nginx.conf was created on Windows, normalize CRLF -> LF.
RUN tmp="$(mktemp)" && tr -d '\r' < /etc/nginx/conf.d/default.conf > "$tmp" && mv "$tmp" /etc/nginx/conf.d/default.conf

ARG SERVER_NAME
ARG WEB_PORT
RUN sed -i 's#{{ SERVER_NAME }}#'$SERVER_NAME'#g' /etc/nginx/conf.d/default.conf
RUN sed -i 's#{{ WEB_PORT }}#'$WEB_PORT'#g' /etc/nginx/conf.d/default.conf