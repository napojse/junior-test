Junior PHP developer test
==========================

Run project on localhost
---------------
- clone this repository
- build containers with `docker-compose`. If you are not using docker yet, download Docker Desktop via https://www.docker.com/products/docker-desktop/ and check documentation on https://docs.docker.com/compose/install/. On Linux, please read also https://docs.docker.com/engine/install/linux-postinstall/
- go to shell with `docker-compose exec php sh`
- install composer dependencies
- project should be ready on URL http://localhost/
- create subdirs `napojse_test/log` and `napojse_test/temp`

Entities and repositories
-------------
- create Doctrine entity `User` into folder `app\Entity` with attributes `$id` (auto increment), `$email` (required unique string), `$password` (required string), `$fullName` (optional nullable string). The repository should be a descendant of `AbstractEntity`
- create Doctrine repository for entity `User` into folder `app\Service`. The repository should be a descendant of `AbstractRepository`
- create Doctrine entity `LoginAttempt` into folder `app\Entity` with attributes `$id` (auto increment), `$user` (many-to-one relation to entity `User`), `$createdAt` (required immutable date time). The repository should be a descendant of `AbstractEntity`
- create Doctrine repository for entity `LoginAttempt` into folder `app\Service`. The repository should be a descendant of `AbstractRepository`
- run Doctrine command and create database tables: `php bin/console orm:schema-tool:create`

Form
-----------
- create a table list of all `User` entities in `HomePresenter:default`
- create a Nette form for creating a new `User` record in `HomePresenter:create`. Form should have fields `fullName`, `email`, `password`. All fields should be required.
- create a database record after form submit and redirect to default view
