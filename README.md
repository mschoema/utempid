# utempid

> Unique temporary id generator for python

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

class TemporaryObject(object):

    gen = UtempidGenerator()

    def __init__(self):
        self.id = self.gen.get_id()

    @classmethod
    def count(cls):
        return cls.gen.active_count

    def __del__(self):
        self.gen.return_id(self.id)


def main():
    a = TemporaryObject() # a.id = 0
    b = TemporaryObject() # b.id = 1
    c = TemporaryObject() # c.id = 2

    print("count: ", TemporaryObject.count()) # 3
    del a # return id 0
    print("count: ", TemporaryObject.count()) # 2

    d = TemporaryObject() # d.id = 0

    print("count: ", TemporaryObject.count()) # 3
    b = 1 # return id 1
    print("count: ", TemporaryObject.count()) # 2
```

License
----

MIT License

Copyright (c) 2019 mschoema

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
