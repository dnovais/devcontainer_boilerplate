# An example Dockerfile for Ruby on Rails development with asdf

### ARGs
ARG DEBIAN_FRONTEND=noninteractive
ARG VARIANT=bullseye

### FROM
FROM mcr.microsoft.com/vscode/devcontainers/base:${VARIANT}

### ENVs
ENV APP_PATH /app
ENV PATH /home/vscode/.asdf/shims:/home/vscode/.asdf/bin:$PATH
ENV ASDF_DATA_DIR /usr/local/asdf

### Install all dependencies you need for your project here
RUN mkdir -p "$APP_PATH" && \
  apt-get update && \
  apt-get -y install --no-install-recommends \
  build-essential gnupg2 tar git zsh libssl-dev zlib1g-dev libyaml-dev curl libreadline-dev \
  postgresql-client libpq-dev openssh-client default-libmysqlclient-dev\
  imagemagick libjpeg-dev libpng-dev libtiff-dev libwebp-dev libvips \
  tzdata gifsicle \
  tmux \
  vim \
  zsh

### Set the workdir
WORKDIR "$APP_PATH"

### Install asdf
RUN git clone https://github.com/asdf-vm/asdf.git /usr/local/asdf && \
  echo 'source /usr/local/asdf/asdf.sh' > /etc/profile.d/asdf.sh && \
  chmod +x /etc/profile.d/asdf.sh && \
  chown -R vscode:vscode /usr/local/asdf

RUN echo -e '\n. /usr/local/asdf/asdf.sh' >> /home/vscode/.bashrc && \
  echo -e '\n. /usr/local/asdf/asdf.sh' >> /home/vscode/.zshrc && \
  echo -e "\nexport PATH=\"/home/vscode/.gems/bin:\$PATH\"" >> /home/vscode/.bashrc && \
  echo -e "\nexport PATH=\"/home/vscode/.gems/bin:\$PATH\"" >> /home/vscode/.zshrc

# # Set the user
# USER app

COPY .tool-versions ./

### SHELL
SHELL ["/bin/zsh", "-lc"]

### Install Ruby and Node.js using asdf
RUN /bin/bash -c ". /usr/local/asdf/asdf.sh && asdf plugin add ruby"
RUN /bin/bash -c ". /usr/local/asdf/asdf.sh && asdf plugin add nodejs"
RUN /bin/bash -c ". /usr/local/asdf/asdf.sh && asdf install ruby 2.7.7"
RUN /bin/bash -c ". /usr/local/asdf/asdf.sh && asdf install nodejs 14.18.2"
RUN /bin/bash -c ". /usr/local/asdf/asdf.sh && asdf global ruby 2.7.7"
RUN /bin/bash -c ". /usr/local/asdf/asdf.sh && asdf global nodejs 14.18.2"

# Change ownership of ASDF installations
RUN chown -R vscode:vscode /usr/local/asdf

USER vscode

### Install bundler
COPY Gemfile Gemfile.lock ./

RUN . /usr/local/asdf/asdf.sh && \
  gem install bundler -v "~> 2.3.26"

### Expose ports
EXPOSE 3000 35729