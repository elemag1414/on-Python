# on-Python
General Info On Python3.x

### Manual Package Installation/Uninstallation

- [Ref](https://stackoverflow.com/questions/1550226/python-setup-py-uninstall)

* Install Package Manually

```bash
$ cd path/to/pacakge
$ sudo python3 setup.py install
```

* Uninstall Package Manually

Record Installed Files
```bash
$ cd path/to/pacakge
$ sudo python3 setup.py install --record files.txt
```

Remove Installed Files via xargs
```bash
$ cd path/to/pacakge
$ sudo xargs rm -rf < files.txt
```

### Tips

* [Convert Avi to mp4](Tips/convertVideo.md)

### Debugging

* [How to Debug Multiple Python files via VSCode](debug.md)
* [Simple Background Removal](background-removal.md)
