FROM docker:dind AS build_docker
FROM maven:latest AS build_maven

#Maven options
ENV MAVEN_OPTS="-DskipTests -Dmaven.repo.local=.m2/repository"
