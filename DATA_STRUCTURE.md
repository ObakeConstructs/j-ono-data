## STRUCTURE
All definition records are stored in a single JSON array in the `j-ono-data.json` file.
```
[
  { definition record },
  { definition record },
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
  "literal": "gara",
  "katakana": [ "ガラ", "ガラッ" ],
  "hiragana": [ "がら", "がらっ" ],
  "definition": [
    {
      "equivalent": "bang, close, open, shut, slide, slam, swish, swoosh, thump",
      "meaning": "the sound of a sliding window or sliding door being opened or shut",
      "example": [ "gara~1a~ガラッ", "gara~1b~ガラッ" ]
    },
    {
      "equivalent": "clatter, clutter, rattle, tumult",
      "meaning": "the sound of something falling apart, collapsing or settling",
      "example": [ "gara~2a~ガラッ" ]
    }
  ]
}
```

## IMAGE FILE
* Each Image File is in a folder corresponding to the first letter of its filename.
* All images are 400 pixels by 400 pixels and contain publisher attribution statements.
* All image formats are exclusively JPEG (`*.jpg`), for the time being.
* Naming convention: `[literal]~[unique id]~[display title].jpg`
  * Underscores are used in lieu of spaces in image filenames.
  * The `[literal]` and `[unique id]` parts are just for keeping the image files organized.
  * The `[display title]` part is displayed as the title of the image in the [J-ONO Search](https://j-ono.com/) tool.
