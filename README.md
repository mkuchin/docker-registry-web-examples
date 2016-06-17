## Example configuration for [docker-registry-web](https://github.com/mkuchin/docker-registry-web)

#### Before start: install docker-compose
    curl -L https://github.com/docker/compose/releases/download/1.7.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose

#### How to run:
    
    curl -L https://github.com/mkuchin/docker-registry-web-examples/releases/download/0.1.0-rc1/examples.tar.gz | tar -xzv
    cd examples/nginx-auth-enabled/
    ./generate-keys.sh
    docker-compose up
    

#### Create test user:
![Creating user](https://raw.githubusercontent.com/mkuchin/docker-registry-web-examples/master/images/create-test.gif)

#### Push some images

    docker login localhost
    docker pull hello-world
    docker tag hello-world localhost/hello-world:latest
    docker tag hyper/docker-registry-web:auth-experimental localhost/docker-registry-web:latest
    docker push localhost/hello-world:latest
    docker push localhost/docker-registry-web:latest

#### and then pull

    docker rmi localhost/hello-world:latest
	docker run localhost/hello-world:latest
	
#### Check web registry for changes

