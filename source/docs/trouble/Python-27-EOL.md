# Python 2.7 end of life problems

```shell
Python 2.7 will reach the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 won’t be maintained after that date. A future version of pip will drop support for Python 2.7.
```

Python 2.7 causes lots of bugs due to end of life. But many scripts in kali (and elsewhere) are still in 2.7. The errors not only occur for 2.7.18, also when using the current Python 3 version on kali (3.9.9). Its a mess. And `pyenv` was not a solution either.

Common errors:

```shell
ImportError: No module named <Package Name>
pip: command not found error
```

## ImportError on NetfilterQueue

```shell
ImportError: No module named netfilterqueue
```

Neither `pip install NetfilterQueue` or `pip3 install NetfilterQueue` work. Not for version 1.0. not for 0.9 (the last version also supporting python2.7). Getting it from `kti` does at the moment (at least for python3).

```shell
kali:~$ sudo apt-get install python3-pip git apache2 tcpdump libnfnetlink-dev libnetfilter-queue-dev
kali:~$ sudo pip3 install --upgrade -U git+https://github.com/kti/python-netfilterqueue
```

## ImportError on Scapy

* [Choose bundle](https://scapy.readthedocs.io/en/latest/installation.html) and install with `pip3` for python 3. 
* Then copy `dist-packages` `scapy` files to a new `scapy` directory in `dist-packages` for python 2.7

