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




# Roadmap
- Write packer/unpacker for Go, Python, C#, C/C++.

# Contribute


# Authors
- Afshin Mehrabani

# License
MIT
