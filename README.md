# utempid

> Unique temporary id generator for python

**Badges will go here**

- build status
- issues (waffle.io maybe)
- devDependencies
- npm package
- coverage
- slack
- downloads
- gitter chat
- license
- etc.

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

## Table of Contents (Optional)

> If you're `README` has a lot of info, section headers might be nice.

- [Installation](#installation)
- [Features](#features)
- [Contributing](#contributing)
- [Team](#team)
- [FAQ](#faq)
- [Support](#support)
- [License](#license)


---

## Example (Optional)

```python
# code away!
gen = utempid.UtempidGenerator()

# get temporary ids
first_id = gen.get_id() # 0
second_id = gen.get_id() # 1
third_id = gen.get_id() # 2

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
