# utempid

> Unique temporary id generator for python

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

---

## Example (Optional)

```python
# import the class
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

---

## Installation

```shell
$ pip install utempid
```

---

## License

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

- **[MIT license](http://opensource.org/licenses/mit-license.php)**
