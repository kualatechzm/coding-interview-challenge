# Software Developer Technical Assessment

This technical assessment forms part of the interview process for a software
developer role at Kuala Tech. It is based around a small demo program that exposes an HTTP API to return requested values from the Fibonacci sequence.

We have packaged it up with a Docker build environment to make it easier for
you to build and run. In order to run it, you'll need to have the `docker`
(and optionally `docker-compose` if not using the new Docker compose plugin) command line
tools installed. You will also need a way of making requests to an HTTP API.
On Unix systems such as Linux and OSX, the
`curl` command line tool should be available. On Windows systems, you will
need to install curl or another tool
(such as [Insomnia](https://insomnia.rest/download)) to interact with the
HTTP API.

Before you start the tasks, it would be worth familiarising yourself with
the demo application. The following shows how to start it up, and a couple
of example queries:

```bash
# Starting the demo app. The first time will be slower as it needs to build.
# From this directory:
docker-compose up -d

# Making requests to the demo app
curl http://localhost:8080/fibonacci?order=4
# Response: {"order":4,"value":3}
curl http://localhost:8080/fibonacci?order=10
# Response: {"order":10,"value":55}

# After making code changes, you will need to force docker-compose to rebuild
# the image rather than just running the one that has already been built
docker-compose up --build -d

# Shutting down the demo app
docker-compose down
```

## Tasks

Now that you are familiar with the demo app and have managed to build and run
it, here are some tasks for you to attempt. We would like to see an attempt
at one of them. Have a read through and choose the task that interests you the
most, and/or the task which will best let you exibit your skills.

Once you have completed your task, please proceed as instructed in [README.md](/README.md). Ahead of the interview, we will look through
your code, and during the interview we will go through your solution together
and ask some questions about it.

### Option 1: Add Recursive Endpoint to Demo App

Currently, the API exposes an endpoint `/fibonacci` that uses an iterative
method for calculating the value of the requested order of the Fibonacci
sequence. Please extend the program to add a second endpoint:
`/recursive-fibonacci`. This endpoint should use a recursive method for
calculating the value.

### Option 2: Create LRU Cache for Demo App

Create a companion app which implements a Least Recently Used (LRU) cache.
The cache app should have the following properties:

- It should be a separate program, not just another endpoint on the demo app
- It should store a maximum of 5 results in the cache
- It should implement a 'least recently used' cache eviction policy.
- If the requested sequence order is already in the cache, it should be returned
- If the requested sequence order is not in the cache then it should be fetched from
  the demo app, stored, and returned.
- It should be built and run using Docker
  - It should be built as a Docker image
  - It should be included in the docker-compose.yml file
- It should listen on port 8081
- It should expose a `/fibonacci` endpoint which caches, and proxies the results
  of the `/fibonacci` endpoint of the demo app.

The message format of the responses from the cache application should be of the form:

```bash
# Request:
curl http://localhost:8081/fibonacci?order=4
# Response (don't worry about indentation, this is just to make it easier to read)
{
    "fibonacci": {
        "order": 4,
        "value": 3
    },
    "cached": true (or false)
}
```

### Option 3: Re-impmement the Demo App in a Language of Your Choice

Implement an app which has equivalent functionality in a language of your choice.
Your re-implementation should satisfy the following constraints:

- It should expose the same HTTP API with an identical `/fibonacci` endpoint
- It should be built and run using Docker
  - It should be built as a Docker image
  - It should be included in the docker-compose.yml file

You may also want to add the `/recursive-fibonacci` endpoint to your implementation.
