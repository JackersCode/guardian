FROM node:16
ENV PLATFORM="docker"
#ENV NODE_ENV="production"

WORKDIR /usr/vc-modules
COPY ./vc-modules/package.json ./
RUN npm install
COPY ./vc-modules/tsconfig.json ./
ADD ./vc-modules/src ./src/.
RUN npm run build

WORKDIR /usr/interfaces
COPY ./interfaces/package.json ./
RUN npm install
COPY ./interfaces/tsconfig.json ./
ADD ./interfaces/src ./src/.
RUN npm run build

WORKDIR /usr/tymlez-service
COPY ./tymlez-service/package.json ./
RUN npm install
COPY ./tymlez-service/tsconfig.json ./
COPY ./tymlez-service/.env.docker ./.env
ADD ./tymlez-service/src ./src/.
RUN npm run build

CMD npm start
