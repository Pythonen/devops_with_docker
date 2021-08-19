FROM ubuntu:18.04 as build_stage

WORKDIR /appdir

COPY ./example-frontend/ .
ENV REACT_APP_BACKEND_URL=http://localhost:8080/ 

RUN apt-get update && apt-get install -y curl && \
	curl -sL https://deb.nodesource.com/setup_14.x | bash && \
	apt install -y nodejs	&& \
	apt-get purge -y --auto-remove curl && \
	rm -rf /var/lib/apt/lists/*
RUN npm install && npm run build && \
  npm cache clean --force


FROM node:alpine
RUN npm install -g serve 
COPY --from=build_stage /appdir/build /appdir/build/
WORKDIR /appdir
COPY --chown=node:node . /appdir/build
USER node
CMD ["serve", "-s", "-l", "5000", "build"]
