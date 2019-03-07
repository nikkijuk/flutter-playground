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

# swagger

Dart generation with swagger codegen in documented here
- https://github.com/swagger-api/swagger-codegen/pull/7406

If you ask yourself why Magento Open API documentation is never outdated read this? Simple: Because they are generated from running software.
- https://devdocs.magento.com/guides/v2.3/rest/bk-rest.html

Magento uses Swagger to generate documentation from it's endpoints. When your local server is running you can try to get this documentation
- https://devdocs.magento.com/guides/v2.3/rest/generate-local.html

Magento API documentation should look like this. You can use for example Postman to test endpoints. Postman can import open api definitions if you want.
- https://devdocs.magento.com/swagger/
