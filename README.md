Homogenius documentation
====
Homogenius is a packing/unpacking technique to reduce the size of homogenous JSON files. 


# Philosophy 
The main point of Homogenius is to prevent repeating keys and values in a homogenous JSON format, so this reduces the size of the JSON file.

Currently we are in the first version of Homogenius and in this initial version, we are going to prevent repeating keys only. Further, we will alter Homogenius so it also prevents repeating values also.

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
  //keys
  ['boo', 'foo', 'bar'],
  //values
  ['val1', 'val2', 'val3'],
  ['val1', 'val2', 'val3']
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
  //keys
  ['boo', 'nested': ['boo_nested', 'foo_nested', 'bar_nested'], 'bar'],
  //values
  ['val1', ['val_nested1', 'val_nested2', 'val_nested3'], 'val2'],
  ['val1', ['val_nested1', 'val_nested2', 'val_nested3'], 'val2']
]
```


# Roadmap
- Packer/unpacker for JavaScript, Go, Python, C#, C/C++, Ruby.

# Contribute


# Authors
- Afshin Mehrabani

# License
MIT
