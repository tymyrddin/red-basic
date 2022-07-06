# Goat and wolf

[Goat and wolf ](https://github.com/WebGoat/WebGoat/wiki) is a deliberately insecure application that allows interested developers just like you to test vulnerabilities 
commonly found in Java-based applications that use common and popular open source components.

WebGoat consists of two applications that work together: WebGoat and WebWolf. WebWolf depends on WebGoat and requires that WebGoat is started first.

Both WebGoat and WebWolf are runnable jar files. Make sure the following ports are available: `80`, `8080`, `9090`, 
`9001` when running locally.

## In a virtual machine of choosing

Fork/Clone the repository, checkout the develop branch, build the artifacts using Java 17 and Maven 3.8+, and run the 
archives.

## Dockers

* [Webgoat Docker](https://hub.docker.com/r/webgoat/goatandwolf)