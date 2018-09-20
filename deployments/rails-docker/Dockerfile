FROM leoapp/leo-rails-docker-base:latest

MAINTAINER Muhammet <dilekmuhammet@gmail.com>

ENV MY_SECRET="my environment variable"

RUN mkdir -p /var/app

WORKDIR /var/app/

ADD Gemfile /var/app/
ADD Gemfile.lock /var/app/

RUN bundle install --without development test

# Add the Rails app
COPY . /var/app/

RUN npm install

RUN RAILS_ENV=production bundle exec rake assets:precompile
RUN RAILS_ENV=production bundle exec rake db:migrate

EXPOSE 80

CMD ["bundle", "exec", "puma", "-C", "config/puma.rb"]