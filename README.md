# S-Pipes-UI editor

> Skeleton is from - React Starter Boilerplate with Hot Module Replacement and Webpack 4


### Building

```
$ npm install
```

IMPORTANT - https://github.com/facebook/create-react-app/issues/10811.
The `npm@7.13.0` version is required and `npm update --force` command.

Will create a `dist` directory containing your compiled code.

Depending on your needs, you might want to do more optimization to the production build.

## Basic info

Run development server

```
$ npm run dev
```


### Dockerization
The docker image of SPipes Editor UI can be built by `docker build -t s-pipes-editor-ui .`

Then, SPipes Editor UI can be run as `docker run -e SERVICE_URL=<SPIPES_BACKEND_URL> -p 3000:80 s-pipes-editor-ui`   
where <SPIPES_BACKEND_URL> denotes the URL where SPipes backend is running.


### Docker-compose
The docker image of SPipes Editor UI can be built by `docker build -t s-pipes-editor-ui .`

The docker-compose is composed of 4 services and can be ruin via `docker-compose up`:
* s-pipes-editor-ui - accessible on `http://localhost:3000`
* s-pipes-editor-rest - manual build of the image is required [repository](https://github.com/chlupnoha/s-pipes-newgen) - accessible on `http://localhost:18115`
* s-pipes-engine - manual build of the image is required [repository](https://github.com/kbss-cvut/s-pipes) - accessible on `http://localhost:8081`
* rdf4j - official [docker image](https://hub.docker.com/r/eclipse/rdf4j-workbench) - accessible on `http://localhost:8080/rdf4j-workbench`

Manual required steps: 
* s-pipes-engine
    * The service does not automatically create the repository in RDF4J, so manual creation of a repository is required.
    * The logging configuration for RDF4j is hardcoded in the image, but it could override via `_pConfigURL` param. However, it is not a convenient format to work. Also both servies must to share volume or the config has to be exposed.

* Notes
    * volumes of `/home:/home` is currently required for sharing the scripts 

![GitHub Logo](public/architecture.png)
Architecture images

###License
Licensed under GPL v3.0.