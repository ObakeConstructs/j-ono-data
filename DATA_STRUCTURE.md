## STRUCTURE
All definition records are stored in a single JSON array in the `j-ono-data.json` file.
```
[  
  { definition record }  
  { definition record }  
  ... etc.  
]
```

That's it.  Nothing fancy.

## DEFINITION RECORD
* Each Definition Record contains...
  * a "literal" translation string
  * an array of "katagana" strings
  * an array of "hiragana" strings
  * an array of "definition" objects
* Each "definition" object contains...
  * an english "equivalent" string
  * a "meaning" string
  * an array of "example" image filename strings.

Example Definition Record:
```
{
  "literal": "fu",
  "katakana": [ "フ", "フッ", "フー", "フーッ" ],
  "hiragana": [ "ふ", "ふっ", "ふー", "ふーっ" ],
  "definition": [
    {
      "equivalent": "chortle, chuckle, ha, heh, laugh",
      "meaning": "a quick, short laugh",
      "example": [ "fu-1a", "fu-1b" ]
    },
    {
      "equivalent": "fade, disappear, vanish",
      "meaning": "to vanish or cause something to vanish",
      "example": ["fu-2"]
    },
    {
      "equivalent": "ease, relief, release, solace",
      "meaning": "an expression of relief",
      "example": ["fu-3"]
    },
    {
      "equivalent": "fwip, fwit, fwoom, pop, shoom, snap, whoom",
      "meaning": "a sudden and/or fast movement",
      "example": ["fu-4"]
    }
  ]
}
```

## IMAGE FILE
* While Image Files are not technically required, we made it a point early on that we didn't want to add any definitions unless we actually had a good representational image to back it up.
* Each Image File is in a folder corresponding to the first letter of its filename.
* All Image File images are 400 pixels by 400 pixels and contain publisher attribution statements.
* All Image File formats are JPEG (`*.jpg`), exclusively.
* Naming Convention: `[literal]~[unique id]~[display title].jpg`
  * Underscores are used in lieu of spaces in image names.
  * The `[literal]` and `[unique id]` parts are just keeping the image files organized.
  * The `[display title]` part is displayed as the title of the image in the [J-ONO Search](https://j-ono.com/) tool.
