# ml-sc

A simple machine learning system consisting of multiple components:
* Frontend App [TypeScript + Angular]
* Gateway [Java + Spring Boot]
* 3 Predictors [Python + scikit-learn]
* Message Broker [Kafka]


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
  Kafka <--> Predictor1;
  Kafka <--> Predictor2;
  Kafka <--> Predictor3;
  end
```
