Ривера Александр Андреевич Домашнее задание к занятию «GitLab»
### Задание 1

Развернул GitLab локально через Vagrant, создал проект `netology-ci`, зарегистрировал и запустил GitLab Runner в режиме Docker.


 Скриншоты


https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/b66f2afc3c2c9e2e926f0ae956fb31fb9cf7b784/img/1.png
https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/b66f2afc3c2c9e2e926f0ae956fb31fb9cf7b784/img/2.png



### Задание 2


Поле для вставки кода...

stages:
  - test
  - build

test:
  stage: test
  image: golang:1.17
  script:
    - go test .

build:
  stage: build
  image: docker:latest
  services:
    - docker:dind
  variables:
    DOCKER_DRIVER: overlay2
  script:
    - docker info
    - docker build -t my-go-app .



Скриншоты
https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/b66f2afc3c2c9e2e926f0ae956fb31fb9cf7b784/img/3.png

https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/b66f2afc3c2c9e2e926f0ae956fb31fb9cf7b784/img/5.png

https://github.com/riveraJ45/sys-pattern-homework-git-hw/blob/b66f2afc3c2c9e2e926f0ae956fb31fb9cf7b784/img/6.png

---
