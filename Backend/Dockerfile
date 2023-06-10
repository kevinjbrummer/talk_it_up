FROM ruby:3.1.3


RUN apt update -qq && apt install -y postgresql-client

WORKDIR /app
COPY ./rails/Gemfile /app/Gemfile
COPY ./rails/Gemfile.lock /app/Gemfile.lock
RUN bundle install

COPY ./rails /app

COPY ./rails/entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]