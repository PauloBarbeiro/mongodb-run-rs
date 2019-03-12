# mongodb-run-rs

This Dockerfile aims to build one MongoDb service to be used in BitBucket Pipelines for testing purposes.
It implements the library run-rs, with is a way to automatize the Mongodb replica set setup.

## Using in Bitbucket Pipeline example
```yaml
image: node:10-alpine

pipelines:
  default:
    - step:
        services:
          - mongo
        script:
          - npm install
          - npm run ci
definitions:
  services:
    mongo:
      image: paulobarbeiro/mongodb-rs
      expose:
        - 27017
        - 27018
        - 27019
      restart: always
```

### References:
https://www.npmjs.com/package/run-rs
