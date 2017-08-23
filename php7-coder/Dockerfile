FROM alpine:edge


ARG BUILD_DATE
ARG VCS_REF

LABEL org.label-schema.build-date=$BUILD_DATE \
  org.label-schema.vcs-ref=$VCS_REF \
  org.label-schema.schema-version="1.0" \
  org.label-schema.name="docker coder" \
  org.label-schema.description="PHP codesniffer for - phpcs & phpcbf" \
  org.label-schema.vcs-url="https://github.com/acidaniel/php7" \
  maintainer="Daniel Serna <acidaniel@gmail.com>"  


MAINTAINER Daniel Serna <acidaniel@gmail.com>

ENV HTTP_PROXY=http://proxy-us.intel.com:911
ENV HTTPS_PROXY=http://proxy-us.intel.com:912

RUN apk add --no-cache \
  php7 \
  php7-apcu \
  php7-ctype \
  php7-phar \
  php7-opcache \
  php7-openssl \
  php7-mbstring \
  php7-json \
  php7-ctype \
  php7-xml \
  php7-zlib \
  curl \
  patch \
  && ln -s /usr/bin/php7 /usr/bin/php \
  && curl -sS https://getcomposer.org/installer | php -- --filename=composer --install-dir=/usr/bin \
  && composer global require "squizlabs/php_codesniffer=*" \
  && ln -s /root/.composer/vendor/squizlabs/php_codesniffer/scripts/phpcs /usr/bin/phpcs \
  && ln -s /root/.composer/vendor/squizlabs/php_codesniffer/scripts/phpcbf /usr/bin/phpcbf 

VOLUME /work
WORKDIR /work

CMD ["phpcs", "--standard=PSR2", "."]
