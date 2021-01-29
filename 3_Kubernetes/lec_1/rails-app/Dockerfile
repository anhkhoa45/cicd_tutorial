FROM ruby:2.5-alpine AS app

ENV LANG C.UTF-8

ENV APP_HOME /app
WORKDIR $APP_HOME

RUN apk add --update --no-cache \
  alpine-sdk \
  build-base \
  tzdata \
  mariadb-dev \
  mariadb-client \
  imagemagick6 \
  imagemagick6-c++ \
  imagemagick6-dev \
  imagemagick6-libs \
  pkgconfig \
  libffi-dev \
  openssl

ARG ENV
ENV RAILS_ENV ${ENV}
ENV BUNDLE_PATH /usr/local/bundle

COPY ./Gemfile* $APP_HOME
RUN bundle install --jobs=4 --path=${BUNDLE_PATH}

COPY . $APP_HOME

CMD ["ash", "-c", "bundle exec rails s -d -p 3000 -b '0.0.0.0'"]
