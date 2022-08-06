# Poison open source supply chains

## Attack tree

```text
1 Create a new package (OR)
    1.1 Develop and publish package (AND)
    1.2 Distribute in dependency trees
        1.2.1 Use a name similar to existing package names (“typosquatting” or “combosquatting”) (OR)
        1.2.2 Reuse an identifier of a project, package, or user account withdrawn by its original maintainer (use after free)
2 Infect an existing package
    2.1 Inject in source (OR)
        2.1.1 Pull request as contributor
        2.1.2 Commit as administrator
            2.1.2.1 Capture credentials or tokens (OR)
            2.1.2.2 Social engineer
    2.2 Inject during build (OR)
        2.2.1 Compromise build system (MitM)
            2.2.1.1 Manipulate package download
            2.2.1.2 Run malicious build
    2.3 Inject in repository system
        2.3.1 Capture credentials or tokens (OR)
        2.3.2 Exploit vulnerabilities
        2.3.3 Deploy in a mirror repository
```

## Articles

* [Backstabber's Knife Collection: A Review of Open Source Software Supply Chain Attacks](https://arxiv.org/abs/2005.09535)

## Mitigations