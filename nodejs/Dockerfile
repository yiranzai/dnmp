FROM node:8-alpine

LABEL maintainer="Luo Di <luodi0128@gmail.com> <https://github.com/lddsb>"

# define variable
ARG CUSTOMIZE_MIRROR
# replace mirror
RUN if [ ${CUSTOMIZE_MIRROR} ]; then \
    sed -i "s/dl-cdn.alpinelinux.org/${CUSTOMIZE_MIRROR}/g" /etc/apk/repositories \
    ;fi
# define variable
ARG HTTPS_MIRROR=false
# mirror http scheme
RUN if [ ${HTTPS_MIRROR} = true ]; then \
    sed -i "s/http:\/\//https:\/\//g" /etc/apk/repositories \
    ;else \
    sed -i "s/https:\/\//http:\/\//g" /etc/apk/repositories \
    ;fi

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

# define variable
ARG NODE_GULP=false
# install gulp
RUN if [ ${NODE_GULP} = true ]; then\
    yarn global add gulp \
    ;fi

# define variable
ARG NODE_SPECIAL_INSTALL
# other commands
ENV NODE_SPECIAL_INSTALL ${NODE_SPECIAL_INSTALL}
RUN if [ $NODE_SPECIAL_INSTALL ]; then \
    ${NODE_SPECIAL_INSTALL} \
    ;fi

EXPOSE 8080
CMD ["npm", "start"]