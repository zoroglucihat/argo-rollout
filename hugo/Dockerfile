# Use an official lightweight Alpine as a parent image
FROM alpine:latest

# Set Hugo version
ENV HUGO_VERSION 0.88.1
ENV HUGO_BINARY hugo_${HUGO_VERSION}_Linux-64bit.tar.gz

# Install Hugo
RUN set -x && \
  apk add --update wget ca-certificates && \
  wget https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/${HUGO_BINARY} && \
  tar xzf ${HUGO_BINARY} && \
  rm -r ${HUGO_BINARY} && \
  mv hugo /usr/bin && \
  apk del wget ca-certificates && \
  rm /var/cache/apk/*

# Create a new directory to run commands from
WORKDIR /usr/share/blog

# Copy the entire project
COPY . /usr/share/blog

# Expose the default Hugo port
EXPOSE 1313

# Run Hugo server
CMD hugo server --bind=0.0.0.0 --baseURL=http://localhost:1313
