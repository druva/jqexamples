# jqexamples

```
[{
		"a": 1,
		"b": ["b1A", "b2A", "b2C"],
		"c": true
	},

	{
		"a": 2,
		"b": ["b1B", "b2B", "b2B"],
		"c": true
	}
]

```
. | map(select(.a ==1))
```
[
  {
    "a": 1,
    "b": [
      "b1A",
      "b2A",
      "b2C"
    ],
    "c": true
  }
]
```
