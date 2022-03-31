# ml-sc

A simple machine learning system consisting of multiple components:
* Frontend App [TypeScript + Angular]
* Gateway [Java + Spring Boot]
* Setup Storage [PostgreSQL]
* Prediction Storage [MongoDB]
* Message Broker [Kafka]
* 3 Predictors [Python + scikit-learn]

#### Source code on GitLab
https://gitlab.com/ml-sc


#### Infrastructure diagram

```mermaid
flowchart TD;
  subgraph CloudFront + S3;
  App;
  end;
  App --> Gateway;
  App <--> Cognito;
  Gateway <--> Cognito;
  subgraph EC2/EKS;
  Gateway <--> Kafka;
  Gateway <--> MongoDB;
  Gateway <--> PostgreSQL;
  Kafka <--> Predictor1;
  Kafka <--> Predictor2;
  Kafka <--> Predictor3;
  end
```
