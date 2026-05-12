FROM ruby:3.4.9-slim-bookworm

RUN apt update && apt install -y gcc build-essential vim \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
  && truncate -s 0 /var/log/*log

WORKDIR /app/docs

RUN gem update --system && gem install bundler -v 4.0.11

COPY docs/Gemfile docs/Gemfile.lock ./
RUN bundle install

CMD ["bundle", "exec", "jekyll", "serve", "-H", "0.0.0.0"]
