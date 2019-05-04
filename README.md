***aion4j***
---

**Aio4j suite of tools are now maintained under [BloxBean](https://github.com/bloxbean) project.
Please visit (https://github.com/bloxbean) for details.

This page is no longer maintained.

This project is currently in conceptual stage. 

Goals
----
- A set of developer tools and frameworks to help smart contract development on Aion Platform. The idea is to leverage on the existing tools (IDE, Frameworks etc.) in java ecosystems. 
- Abstract all the complexities of blockchain interaction from a java application and provide a POJO / Interface based programming model.
- Enable java developers with familiar tools to iterate faster during development with a relatively smaller learning curve. (Through an embedded FastVM runtime and libraries)
- Help developers to develop with their existing java development tools.


1. [**Aion FastVM Docker**](https://github.com/satran004/aion-fastvm-docker) -  Docker container for Aion FastVM / Solidity compiler. Use this to quickly compile your Solidity .sol smart contracts for the Aion Network. It supports cross OS compilation of solidity contracts for Aion. 

(Status: Ready to use)

2. [**Aion4j docker**](https://github.com/satran004/aion4j-docker) - This docker container provides all the required libraries/tools for development on Aion platform. The idea is to provide a containerized smart contract development environment where developer can both compile and unit test their smart contract without deploying on the actual blockchain. As currently solidity compiler on Aion is only supported on Ubuntu, the dockerized approach will be helpful for non-Ubuntu developers. 

(Status: Not ready)

3. [**Aion4j-core**](https://github.com/satran004/aion4j-core) - It provides a client-side library which uses aion java rpc api to interact with Aion blockchain. 
The initial version of this library will help developers to unit test their solidity contracts using any existing java testing framework and an embedded FastVM instance. Developers should be able to use their preferred java testing framework. With an embedded Fast VM or dummy blockchain, the developer can test their smart contract in a deterministic way.

- This framework will provide a java interface/POJO based programming model to interact with the smart contract. For each smart contract, an equivalent java interface will be defined with all the required methods of solidity contract. (This interface can be auto-generated through a maven / gradle plugin)
- The framework will dynamically generate an implementation for the interface during runtime (by creating a proxy / delegate through byte code manipulation libraries). 
- Developer can obtain an instance of generated proxy class (by passing the interface) from the framework library and interact with it to deploy/invoke different methods in the smart contract.
- The generated proxy object should be able to convert all input params from java types to solidity types while passing to the actual contract and similarly convert the return objects in solidity to java types.
- In the initial version, the proxy implementation will be supported for an embedded FastVM based dummy blockchain. This can  be used for the smart contract unit testing. So the first phase of this library only aims  to support unit testing for smart contracts.
- In the later version, the proxy implementation will be enhanced to support actual blockchain (remote). So developer can use  same interface based programming model but will be connected to a remote blockchain during runtime.
The implementation (embedded or remote) will be decided through the available configuration parameters during runtime without changing any java code.

The goal is to support the same programming model to interact with both an embedded and actual blockchain deployment.

(Status: Not ready)

The concept is similar to one of the [earlier proposal](https://github.com/satran004/aion-spring-proposal/wiki/Proposal), but much simpler and without any Spring framework dependency. 

4. [**Aion4j-maven-plugin**](https://github.com/satran004/aion4j-maven-plugin) A maven plugin to do most of the manual steps like

     - Interface code generation from solidity source file
     - Initializing environment by automatically deploying aion libraries to local m2 repository
     - Run tests
     
     The maven plugin will help to bring all of the above tools / frameworks and existing tools together.

(Status: No ready)
     
     
**5. IDE :** The goal is leverage on the existing IDE or IDE plugins. There are solidity plugins available for IDEs like Intellij and eclipse. So those plugins can be used for editor support for Solidity.  
The developer should be able to run his IDE on the host OS even if he/she is using docker container for Aion4j docker runtime. To achieve this, docker volume service will be used to map host file system with the container fs.

(Status: Not ready)













