[:back:](/home)
---

# Tips and tricks
This page collects little tips and tricks that make the handling and the development with ExOT easier.

## Modifying runtime objects

Make it possible to extend, e.g. layers, inline by writing a new method and then overwriting the method in the object. As in the example below:

```python
class Test(object):
    def __init__(self, a):
        self._a = a
    def get(self):
        return self._a
myobj = Test(100)
myobj.get()
-> 100
def newget(self):
    return self._a * 2
myobj.get = types.MethodType(newget, myobj)
myobj.get()
-> 200
```