#
# Copyright (c) 2021 Red Hat, Inc.
# This program and the accompanying materials are made
# available under the terms of the Eclipse Public License 2.0
# which is available at https://www.eclipse.org/legal/epl-2.0/
#
# SPDX-License-Identifier: EPL-2.0
#

ARG BASE_IMAGE="docker.io/php:8.1.1-cli"

FROM docker.io/php:8.1.1-cli

RUN apt-get update \
    && apt-get -y install \
        libmariadb-dev \
        zlib1g-dev \
        libzip-dev \
        git zip unzip

RUN pecl install redis \
    && pecl install xdebug \
    && docker-php-ext-enable redis xdebug

RUN docker-php-ext-install pdo_mysql mysqli zip

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

#{INCLUDE:../base.dockerfile}
