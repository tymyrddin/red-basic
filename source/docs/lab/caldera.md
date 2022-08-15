# Red and blue teaming with Mitre Att&ck Caldera

## Installation

    git clone https://github.com/mitre/caldera.git --recursive --branch 4.0.0

Build the image:

    docker compose build

And run:

    docker run -p 7010:7010 -p 7011:7011/udp -p 7012:7012 -p 8888:8888 caldera:latest

`http` interface available on `localhost:8888` with username: red, password: admin.

[Configure the server](https://caldera.readthedocs.io/en/latest/Server-Configuration.html) 
and rebuild.

## Aaaand play! 

[Mitre Att&ck](https://attack.mitre.org/) provides a list of all the Tactics, Techniques and Procedure 
(TTPs) for these games. 

### Implant an agent inside the target system

* Campaigns -> Agents -> Deploy an agent
* Choose an agent (Sandcat)
* Choose OS (Windows, Linux or Darwin=macOS)
* Copy the generated script and execute on target

### Abilities

* Campaigns -> Abilities
* An ability is a specific ATT&CK tactic/technique implementation which can be executed on running agents. Abilities will include the command(s) to run, the platforms/executors the commands can run on, payloads to include, and a reference to a module to parse the output on the caldera server.
* Use the filter options to see what is all possible. 

### Get the flags

Use [Mitre Att&ck](https://attack.mitre.org/), [the getting started documentation](https://caldera.readthedocs.io/en/latest/Getting-started.html), 
and your wits and get all the flags. After having played and built knowledge on all kinds of scenarios and existing 
attacker types in caldera, gather intelligence on a particular real-life adversary's TTP's and add.


## Graceful termination

To gracefully kill the docker container, find the container process ID for your docker container running caldera

    docker ps

And send interrupt signal, for example `docker kill --signal=SIGINT 5b9220dd9c0f`

    docker kill --signal=SIGINT [container ID]

