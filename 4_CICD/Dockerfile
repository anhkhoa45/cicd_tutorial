FROM ruby:2.7.1-alpine AS app

ENV LANG C.UTF-8

ENV APP_HOME /app
WORKDIR $APP_HOME

RUN apk add --update --no-cache \
  alpine-sdk \
  build-base \
  sqlite-dev \
  nodejs \
  yarn \
  tzdata

ARG ENV
ENV RAILS_ENV ${ENV}
ENV BUNDLE_PATH /usr/local/bundle

COPY rails/Gemfile* $APP_HOME
RUN bundle install --jobs=4 --path=${BUNDLE_PATH}

COPY rails/package*.json $APP_HOME
RUN yarn install

COPY rails $APP_HOME

CMD ["ash", "-c", "bundle exec rails s -p 3000 -b '0.0.0.0'"]
