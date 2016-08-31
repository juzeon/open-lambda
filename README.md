# OpenLambda

OpenLambda is a project dedicated to bringing the Lambda ("serverless") computing framework to the open source world. The purpose of this is primarily to provide a platform for the exploration of research questions that serverless computing prompts (see the publication section).

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Installation

Grab and extract the open-lambda source package from github

```
wget https://github.com/open-lambda/open-lambda/archive/v0.1.0.tar.gz 
```

Use the startup script to install requirements, build the project.

```
cd open-lambda-0.1.0
./tools/quickstart/startup.sh
make
```

### Starting a lambda cluster locally
Use the start-cluster script to start a local cluster for testing. The cluster will use the Docker registry by default, or the OpenLamdba code registry if passed the optional flag.

```
./util/start-cluster.py [--olregistry]
```

Use the setup.py script to push application handler code to the registry and run startup scripts (must be in a directory under the applications directory).

```
./util/setup.py pychat lambda_func.py
```

Send RPCs to the URL generated by the setup.py script.

```
cat applications/pychat/static/config.json
curl -w "\n" <URL> -d '{"op": "init"}'
curl -w "\n" <URL> -d '{"op": "updates", "ts": "0"}'
curl -w "\n" <URL> -d '{"op": "msg", "msg": "hello"}'
```

## Running the tests

To run the full suite of tests:

```
make test
```

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

## Built With

* Docker
* go-dockerclient
* Nginx
* gRPC

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Authors

* **Tyler Harter** - *Initial work* - [tylerharter](https://github.com/tylerharter)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the Apache License - see the [LICENSE.md](LICENSE.md) file for details 
