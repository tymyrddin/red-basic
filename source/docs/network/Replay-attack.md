# Replay attack

## Attack tree

```text
1 External attack
    1.1 Interleaving
        1.1.1 Deflection
            1.1.1.1 Reflection to sender
            1.1.1.2 Deflection to third party
        1.1.2 Straight replay
    1.2 Classic replay
        1.2.1 Deflection
            1.2.1.1 Reflection to sender
            1.2.1.2 Deflection to third party
        1.2.2 Straight replay
2 Internal attack
    2.1 Deflection
        2.1.1 Reflection to sender
        2.1.2 Deflection to third party
    2.2 Straight replay
```

## Notes

* The origin of a replay attack can be either internal or external to the running process.
* The destination of a replay attack can either be deflected, or sent straight through.
* Interleaving messages from one process are being injected concurrently into another process
* Classic Replays do not depend on the time of the session