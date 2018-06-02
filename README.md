# Filter
. | map(select(.a ==1))
Input
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
Output
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

# Add to arry

.data.messages += [{"a": 11}]
````
{
    "report": "1.0",
    "data": {
        "date": "d",
        "messages": [{
            "d": "d",
            "xml": "x",
            "status": "s",
            "message": "m1"
        }, {
            "d": "d",
            "status": "s2",
            "message": "m2"
        }]
    }
}
```
Output
```
{
  "report": "1.0",
  "data": {
    "date": "d",
    "messages": [
      {
        "d": "d",
        "xml": "x",
        "status": "s",
        "message": "m1"
      },
      {
        "d": "d",
        "status": "s2",
        "message": "m2"
      },
      {
        "a": 11
      }
    ]
  }
}

```


# Filter
. | to_entries[] | select(.key == "b") | .value | .[] | select(.t == "mtb") | .f
returns rb

[. | to_entries[]] | map(select(.value[] | .t == "ct"))[] | .key
returns
a

[[. | to_entries[]] | map(select(.value[] ))[] | .key] | unique
["a","b"]

```
{
	"a": [{
			"f": "ra",
			"t": "m"
		},
		{
			"f": "cf",
			"t": "ct"
		}
	],
	"b": [{
			"f": "rb",
			"t": "mtb"
		},
		{
			"f": "cfb",
			"t": "ctb"
		}
	]
}
```
result
"rb"






# Format Change example
```
[.[] | .bran as $n | .active as $a | .Emp[] | {k:$n, v:., a:$a}]
```
```
[{
		"bran": "branch1",
		"Emp": ["Ren", "Ken", "Ron"],
		"active": true
	},

	{
		"bran": "branch2",
		"Emp": ["Kel", "Pel", "Bel"],
		"active": false
	}]
```

```
[
  {
    "k": "branch1",
    "v": "Ren",
    "a": true
  },
  {
    "k": "branch1",
    "v": "Ken",
    "a": true
  },
  {
    "k": "branch1",
    "v": "Ron",
    "a": true
  },
  {
    "k": "branch2",
    "v": "Kel",
    "a": false
  },
  {
    "k": "branch2",
    "v": "Pel",
    "a": false
  },
  {
    "k": "branch2",
    "v": "Bel",
    "a": false
  }
]

```
