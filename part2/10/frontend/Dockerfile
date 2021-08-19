FROM node:14

#RUN curl -sL https://deb.nodesource.com/setup_14.x | bash sudo apt install -y nodejs

COPY ./example-frontend/ .

EXPOSE 5000

RUN npm install && npm install -g serve

ENV API_URL=http://localhost:8000

RUN npm run build


CMD ["serve","-s","-l","5000","build"]
