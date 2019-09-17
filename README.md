# utempid

> Unique temporary id generator for python

---

## Usage

### Getting it
To download utempid, simply use Pypi via pip.

```shell
$ pip install utempid
```

### Using it

```python
# import the generator class
from utempid import UtempidGenerator

# create the generator
gen = utempid.UtempidGenerator()

# get temporary ids
first_id = gen.get_id() # first_id = 0
second_id = gen.get_id() # second_id = 1
third_id = gen.get_id() # third_id = 2

# return ids when no longer needed
gen.return_id(second_id)

# track amount of temporary ids in use
print(gen.active_count) # 2
```

### Example

UtempidGenerator can be used when creating temporary objects with unique ids.
When an object is destroyed, the id is returned to the generator.
This allows for an easy count of the live objects and creates ids that are limited by the maximum amount of live objects at any point.

```python
# import the generator class
from utempid import UtempidGenerator

class TestObject(object):
    """docstring for TestObject"""
    gen = UtempidGenerator()

    def __init__(self):
        super(TestObject, self).__init__()
        self.id = self.gen.get_id()

    def get_id(self):
        return self.id

    @classmethod
    def count(cls):
        return cls.gen.active_count

    def __del__(self):
        self.gen.return_id(self.id)


def main():
    a = TestObject()
    b = TestObject()
    c = TestObject()
    d = TestObject()

    print(a.get_id()) # 0
    print(b.get_id()) # 1
    print(c.get_id()) # 2
    print(d.get_id()) # 3

    print("count: ", TestObject.count()) # 4
    del a
    print("count: ", TestObject.count()) # 3

    e = TestObject()

    print(e.get_id()) # 0

    print("count: ", TestObject.count()) # 4
    b = 1
    print("count: ", TestObject.count()) # 3
```

---

License
----

MIT License

Copyright (c) 2018 Joel Barmettler

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.