FROM ubuntu:18.04

WORKDIR /usr/src/app

COPY ./example-frontend/ .
ENV REACT_APP_BACKEND_URL=http://localhost:8080/ 

RUN apt-get update && apt-get install -y curl && \
	curl -sL https://deb.nodesource.com/setup_14.x | bash && \
	apt install -y nodejs	&& \
	apt-get purge -y --auto-remove curl && \
	rm -rf /var/lib/apt/lists/*

RUN npm install && npm run build && npm install -g serve && \
  npm cache clean --force

CMD ["serve", "-s", "-l", "5000", "build"]

EXPOSE 5000
