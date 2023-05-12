FROM node:lts-alpine
WORKDIR /usr/src/app
COPY curriculum-back/package*.json ./
RUN npm install
COPY curriculum-back ./
ENV NODE_OPTIONS="--openssl-legacy-provider"
RUN ls -l
CMD ["npm", "run", "prod"]
