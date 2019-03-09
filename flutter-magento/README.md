# flutter-magento

It makes sense to combine old backends to new user interfaces to create seamless experiences for mobile users.

# software stack for experiment


Flutter 
- Flutter is mobile development framework, which uses dart as programming language.

Magento 
- Magento is e-commerse suite, which is developed with PHP, but happens to offer Rest API with Open Api (swagger) definitions for integration.

Swagger 
- Swagger (Open Api) generator and Magentos Api definitions can be used to generate Dart client code for Flutter Mobile Client.

Docker
- Magento can be started using Docker Compose, so that several ready made images are running at local machine.

# flutter

There are some test projects similar to this one
- https://github.com/troublediehard/magento-flutter

It might be good idea to try these projects before going forward with own implementation.

# magento

Use latest Magento 2.X.
- https://devdocs.magento.com/#/individual-contributors

You should first setup magento installation. Easiest way might be to test with trial cloud license. There's many providers for hosted magento, just select one. 
- https://www.fastcomet.com/magento-demo

In long run local development environment is needed. So, just see if your computer is able to run all components and get going with Docker.

# docker 

Magento development setup consists quite some docker images. This might be impractical.
- https://devdocs.magento.com/guides/v2.3/cloud/docker/docker-development.html

There's several providers of docker compose files. With Docker compose it's possible to build and build, start and stop several simultaneously.

Alex Cheng
- https://hub.docker.com/r/alexcheng/magento2
- https://github.com/alexcheng1982/docker-magento2

Bitnami
- https://hub.docker.com/r/bitnami/magento/
- https://github.com/bitnami/bitnami-docker-magento

Magento official
- https://github.com/magento/magento-cloud-docker

Selection criteria: easiest setup with usable test data for our test case. Or just pick first that works. See that it was updated frequently.

## magento & docker compose recipe

I decided to give try to alex chengs docker images for magento 2. Winning points: lot of users, test data provided
- https://github.com/alexcheng1982/docker-magento2

Docker compose was already installed as part of Docker Desktop for Mac.
- https://www.docker.com/products/docker-desktop

Recipe starts from point when whole repository has been fetched with git client to local workspace. 
I used IntelliJ Idea to get sources, but Android Studio would go as well. 
I used Ideas Terminal Tab to type in exactly these commands. 

    $ docker-compose up -d # builds images and strarts them

    $ docker container ls # lists containers running and images they are based
    
    CONTAINER ID        IMAGE                   COMMAND                  CREATED             STATUS              PORTS                            NAMES
    64a640ec15a1        alexcheng/magento2      "/sbin/my_init"          5 hours ago         Up 5 hours          0.0.0.0:80->80/tcp               docker-magento2_web_1
    931db5fb9106        phpmyadmin/phpmyadmin   "/run.sh supervisord…"   5 hours ago         Up 5 hours          9000/tcp, 0.0.0.0:8580->80/tcp   docker-magento2_phpmyadmin_1
    053ded4d9768        mysql:5.6.23            "/entrypoint.sh mysq…"   5 hours ago         Up 5 hours          3306/tcp                         docker-magento2_db_1

    $ docker exec -it 64a640ec15a1 install-magento # note that alexcheng/magento2 container is used to execute command

    $ docker exec -it 64a640ec15a1 install-sampledata # sample data added    

    $ sudo nano /etc/hosts # added local.magento as host to osx's condiguration file
    
    127.0.0.1       local.magento

And then I opened in browser http://local.magento and surprise surprise my shop was there. 
I now have shop running on my local mbp 2017, 16 gb, box. 
My new shop      isn't really fast, but hey: it's all running in 4-core i7 laptop. 

BTW. If you don't want to install Idea or Android Studio, but want to use fancy tools to get sources just use Sourcetree.
- https://www.sourcetreeapp.com/

# swagger

Dart generation with swagger codegen in documented here
- https://github.com/swagger-api/swagger-codegen/pull/7406

If you ask yourself why Magento Open API documentation is never outdated read this? Simple: Because they are generated from running software.
- https://devdocs.magento.com/guides/v2.3/rest/bk-rest.html

Magento uses Swagger to generate documentation from it's endpoints. When your local server is running you can try to get this documentation
- https://devdocs.magento.com/guides/v2.3/rest/generate-local.html

Magento API documentation should look like this. You can use for example Postman to test endpoints. Postman can import open api definitions if you want.
- https://devdocs.magento.com/swagger/
