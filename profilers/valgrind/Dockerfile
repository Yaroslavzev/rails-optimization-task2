FROM ruby:3.3.1

RUN apt-get update && apt-get install g++ valgrind -y \
        massif-visualizer \
        --no-install-recommends \
        && apt-get purge --auto-remove -y curl \
        && rm -rf /var/lib/apt/lists/* \
        && rm -rf /src/*.deb

RUN groupadd -r massif && useradd -r -g massif massif \
    && mkdir -p /home/massif/test && /bin/bash -c 'chown -R massif:massif /home/massif'
USER massif
WORKDIR /home/massif/test

COPY Gemfile /home/massif/test
RUN bundle install