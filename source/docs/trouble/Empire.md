# Empire cannot import name 'Mapping' from 'collections'

The `Mapping` type was moved to `collections.abc` in Python 3.10.

For
```text
...
  File "/usr/local/lib/python3.10/dist-packages/urllib3/util/wait.py", line 1, in <module>
    from .selectors import (
  File "/usr/local/lib/python3.10/dist-packages/urllib3/util/selectors.py", line 14, in <module>
    from collections import namedtuple, Mapping
ImportError: cannot import name 'Mapping' from 'collections' (/usr/lib/python3.10/collections/__init__.py)
```

In `/usr/local/lib/python3.10/dist-packages/urllib3/util/selectors.py`, change

    from collections import namedtuple, Mapping

to

    from collections.abc import Mapping
    from collections import namedtuple

And for 

```text
...
  File "/usr/local/lib/python3.10/dist-packages/urllib3/_collections.py", line 2, in <module>
    from collections import Mapping, MutableMapping
ImportError: cannot import name 'Mapping' from 'collections' (/usr/lib/python3.10/collections/__init__.py)
```

In `/usr/lib/python3.10/collections/__init__.py`, add:

    from collections.abc import Mapping
  