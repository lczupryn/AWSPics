FROM lambci/lambda:build

# working folder
RUN mkdir /build
WORKDIR /build

# install dependencies (highly cacheable)
COPY package.json /build/package.json
RUN git clone git://github.com/http-auth/http-auth.git
RUN cd http-auth
RUN npm install --production
RUN cd ..
RUN npm install --production

# add source code
COPY index.js /build/index.js

# zip entire context and stream output
RUN zip -r /build/dist.zip . > /dev/null
CMD ["cat", "/build/dist.zip"]
