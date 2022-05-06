FROM nginx:1.19.1-alpine

ENV TZ Asia/Taipei
RUN apk --no-cache add tzdata \
    && cp "/usr/share/zoneinfo/$TZ" /etc/localtime \
    && echo "${TZ}" > /etc/timezone

RUN apk add python py-pip && \
    pip install supervisor supervisor-stdout

# Supervisor config
COPY ./supervisord.conf /etc/supervisord.conf

# Copy Scripts
COPY ./start.sh /start.sh

EXPOSE 80
EXPOSE 443

CMD ["sh","/start.sh"]

WORKDIR /www