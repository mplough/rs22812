# rs22812

This project has been exported from the archives at <https://code.google.com/p/rs22812>. I am not the author of this software, but just a end-user whom finds this software invaluable for his own works.

## usage

* Dependencies
  - `python2.6`
    - `python2-pyserial` for `rs22812.py` and `rs22812_linux.py`
    - `wxpython2.8` for `meter.py` (WIP)

### Linux

```shell
cd "$HOME/Projects"
git clone "https://github.com/i8degrees/rs22812.git" rs22812
cd "rs22812"
python2 rs22812_linux.py --port /dev/ttyUSB0
```

#### Arch Linux

```shell
pamac install python2-pyserial
# TODO(jeff): I have yet to try the WX GUI app at meter.py and will post an update
# once I have figured what packages need to be installed.
```

### Windows

I have not tested this as I do not have easy access to a Windows development workstation. Feel free to chime in on this project's **Issues**.

```shell
python2 rs22812.py --port 1
```
