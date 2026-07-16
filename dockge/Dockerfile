FROM louislam/dockge:1

USER root

ARG GIT_USER_NAME
ARG GIT_USER_EMAIL

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        openssh-client \
        nano \
        ncurses-term \
    && rm -rf /var/lib/apt/lists/*

# Make terminal apps like nano work in Dockge's web console
RUN echo 'export TERM=xterm-256color' >> /root/.bashrc

# Rewrite GitHub HTTPS clone URLs to SSH automatically
RUN git config --system url."git@github.com:".insteadOf "https://github.com/" \
    && git config --system --add url."git@github.com:".insteadOf "http://github.com/" \
    && git config --system user.name "$GIT_USER_NAME" \
    && git config --system user.email "$GIT_USER_EMAIL"
