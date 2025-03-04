# Cakeshop

[![Build Status](https://travis-ci.com/jpmorganchase/cakeshop.svg?branch=master)](https://travis-ci.com/jpmorganchase/cakeshop)

An integrated development environment and SDK for Ethereum-like ledgers

![screenshot](docs/images/console.png "screenshot")

![screenshot](docs/images/sandbox.png "sandbox screenshot")

## What is it?

_Cakeshop_ is a set of tools and APIs for working with [Ethereum](https://ethereum.org/)-like ledgers, packaged as a Java web application archive (WAR) that gets you up and running in under 60 seconds.

Cakeshop will download the latest version of [quorum](https://github.com/jpmorganchase/quorum) and bootnode from [geth](https://github.com/ethereum/go-ethereum) (to use a different version, see [here](docs/configuration.md#custom-quorum-binaries)). The cakeshop package includes the [tessera](https://github.com/jpmorganchase/tessera) and [constellation](https://github.com/jpmorganchase/constellation) transaction managers, a [Solidity](https://solidity.readthedocs.org/en/latest/)
compiler, and all dependencies.

It provides tools for managing a local blockchain node, setting up clusters,
exploring the state of the chain, and working with contracts.

## Download

Binary packages are available for macOS and Linux platforms on the [releases](https://github.com/jpmorganchase/cakeshop/releases) page.

## Quickstart

### Requirements

* Java 8+
* NodeJS (if the nodejs binary on your machine isn't called 'node', see [here](docs/configuration.md#nodejs-binary))

### Running via Spring Boot

* Download WAR file
* Run `java -jar cakeshop.war`
* Navigate to [http://localhost:8080/](http://localhost:8080/)


### Running via Docker -- NEEDS UPDATE

Run via docker and access UI on [http://localhost:8080/](http://localhost:8080/)

```sh
docker run -p 8080:8080 quorumengineering/cakeshop
```

You'll probably want to mount a data volume:

```sh
mkdir data
docker run -p 8080:8080 -v "$PWD/data":/opt/cakeshop/data quorumengineering/cakeshop
```

Running under a specific environment

```sh
docker run -p 8080:8080 -v "$PWD/data":/opt/cakeshop/data \
    -e JAVA_OPTS="-Dspring.profiles.active=local" \
    quorumengineering/cakeshop
```

Note that DAG generation will take time and Cakeshop will not be available until it's complete. If you already have a DAG for epoch 0 in your `$HOME/.ethash` folder, then you can expose that to your container (or just cache it for later):

```sh
docker run -p 8080:8080 -v "$PWD/data":/opt/cakeshop/data \
    -v $HOME/.ethash:/opt/cakeshop/.ethash \
    quorumengineering/cakeshop
```

## Further Reading

Further documentation can be found on the [wiki](https://github.com/jpmorganchase/cakeshop/wiki/) and in the [docs](docs/) folder.

## See Also

* [JIF Dashboard](https://github.com/jpmorganchase/jif-dashboard) - The Cakeshop UI was built using the JIF Dashboard framework.

* [solc-cakeshop-cli](https://github.com/jpmorganchase/solc-cakeshop-cli) - The solidity compiler used behind the scenes is `solc-cakeshop-cli`, a thin wrapper atop the [solc](https://github.com/ethereum/solc-js) JS binding.

## Contributing

Thank you for your interest in contributing to Cakeshop!

Cakeshop is built on open source and we invite you to contribute enhancements. Upon review you will be required to complete a Contributor License Agreement (CLA) before we are able to merge. If you have any questions about the contribution process, please feel free to send an email to [quorum_info@jpmorgan.com](mailto:quorum_info@jpmorgan.com).

## License

Copyright (c) 2016-2019 JPMorgan Chase and/or applicable contributors

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

See the [LICENSE](LICENSE) and [THIRD_PARTY](THIRD_PARTY) files for additional license information.
