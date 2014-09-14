Homogenius documentation
====
Homogenius is a packing/unpacking technique to reduce the size of homogenous JSON files. 


# Philosophy 
The main point of Homogenius is to prevent repeating keys and values in a homogenous JSON format, so this reduces the size of the JSON file.

Currently we are in the first version of Homogenius and in this initial version, we are going to prevent repeating keys only. Further, we will alter Homogenius so it also prevents repeating values.

# How it works

Suppose following JSON file:

```js
[{
  'boo': 'val1',
  'foo': 'val2',
  'bar': 'val3'
}, {
  'boo': 'val1',
  'foo': 'val2',
  'bar': 'val3'
}]
```

Above JSON file will be like following after packing:

```js
[
    [{
        "boo": 1
    }, {
        "foo": 1
    }, {
        "bar": 1
    }],
    [
        ["val1"],
        ["val2"],
        ["val3"]
    ],
    [0, 0, 0],
    [0, 0, 0]
]
```

Also, it works perfectly with nested JSON keys and values:

```js
[{
  'boo': 'val1',
  'nested': {
    'boo_nested': 'val_nested1',
    'foo_nested': 'val_nested2',
    'bar_nested': 'val_nested3'
  },
  'bar': 'val2'
}, {
  'boo': 'val1',
  'nested': {
    'boo_nested': 'val_nested1',
    'foo_nested': 'val_nested2',
    'bar_nested': 'val_nested3'
  },
  'bar': 'val2'
}]
```

And it will be:

```js
[
    [{
        "boo": 1
    }, {
        "nested": [{
            "boo_nested": 1
        }, {
            "foo_nested": 1
        }, {
            "bar_nested": 1
        }]
    }, {
        "bar": 1
    }],
    [
        ["val1"],
        [
            ["val_nested1"],
            ["val_nested2"],
            ["val_nested3"]
        ],
        ["val2"]
    ],
    [0, [0, 0, 0], 0],
    [0, [0, 0, 0], 0]
]
```

# Implementations

- [JavaScript (NodeJs + Browser)](https://github.com/homogenius/javascript)

# Roadmap
- Packer/unpacker for <em style="text-decoration: line-through;">JavaScript</em>, Go, Python, C#, C/C++, Ruby.

# Contribute


# Authors
- Afshin Mehrabani

# License
MIT
