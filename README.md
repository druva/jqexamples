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

Filter
. | to_entries[] | select(.key == "b") | .value | .[] | select(.t == "mtb") | .f
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

