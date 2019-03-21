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

NOTES: didn't manage to get "troublediehard/magento-flutter" test project to function - for some reason same call which did work with curl (to get configuration from magento2) didn't work from flutter -- hmm.. 

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

Whole repository needs to be fetched with git client to local workspace. 
I used IntelliJ Idea to get sources, but Android Studio would go as well. 

I used Ideas Terminal Tab to type in exactly these commands at root directory of sources. 

    $ docker-compose up -d # builds images and starts them

    $ docker container ls # lists containers running and images they are based
    
    CONTAINER ID        IMAGE                   COMMAND                  CREATED             STATUS              PORTS                            NAMES
    64a640ec15a1        alexcheng/magento2      "/sbin/my_init"          5 hours ago         Up 5 hours          0.0.0.0:80->80/tcp               docker-magento2_web_1
    931db5fb9106        phpmyadmin/phpmyadmin   "/run.sh supervisord…"   5 hours ago         Up 5 hours          9000/tcp, 0.0.0.0:8580->80/tcp   docker-magento2_phpmyadmin_1
    053ded4d9768        mysql:5.6.23            "/entrypoint.sh mysq…"   5 hours ago         Up 5 hours          3306/tcp                         docker-magento2_db_1

    $ docker exec -it 64a640ec15a1 install-magento # 64a640ec15a1 container (alexcheng/magento2) executes command

    $ docker exec -it 64a640ec15a1 install-sampledata # sample data added    

    $ sudo nano /etc/hosts # added local.magento as host to osx's condiguration file
    
    127.0.0.1       local.magento

At that point I opened magento, and surprise surprise my shop was there. 
- http://local.magento

It's pretty interesting to see admin ui, but for this I need password, which is stored at environment.

    $ docker exec -it 462a673efb94 env # find environment variables 
    
    MAGENTO_ADMIN_USERNAME=admin
    MAGENTO_ADMIN_PASSWORD=magentorocks1

We can see that admin ui works with admin user and proper password
- http://local.magento/admin

Now it's time to check if rest api functions. Let's start with oauth authentication token.
- https://devdocs.magento.com/guides/v2.3/rest/tutorials/orders/order-admin-token.html

Tasks to do is to give admin username and password in json body of http post request to get OAUTH token. 

    $ curl -i -X POST -H "Content-Type: application/json" -d '{"username":"admin","password":"magentorocks1"}' http://local.magento/rest/default/V1/integration/admin/token

    "h51a2pzjftle1sukfh2xzx6h6a1tsr5y"

Call should return token to you. Now test that credentials work by fetching store config. 

    $ curl -i -X GET -H "Content-Type: application/json" -H "Authorization: Bearer h51a2pzjftle1sukfh2xzx6h6a1tsr5y"  http://local.magento/rest/default/V1/store/storeConfigs

    <return configuration as json or authorization error if oauth token has timed out>

One could use Postman here instead of curl, in which case exporting open api definitions to Postman makes experimenting simple.
- https://blog.getpostman.com/2018/12/11/postman-supports-openapi-3-0/

If you wondered how to know right url see your local API definitions 
- https://devdocs.magento.com/guides/v2.3/rest/generate-local.html
- http://local.magento/swagger/

Or see developer documentation 
- https://devdocs.magento.com/

And API documentation of latest Magento version
- https://devdocs.magento.com/swagger/

After all this experimenting it's time for shutdown

    $ docker-compose down # stop all

But wait: What if I'd need to change configuration or want to start again from clean state? 
Just made needed changes to images and rebuild.

    $ docker-compose up --build -d # rebuilds images and starts them

After each start of containers test data and installation needs to be initialized again, but as said this is not big deal.

I now have shop running on my local mbp 2017, 16 gb, box. My new shop isn't really fast, but hey: it's all running in 4-core i7 laptop. 

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
