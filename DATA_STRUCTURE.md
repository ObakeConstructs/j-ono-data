J-ONO keeps all its data in within two JSON files: a "sources" file (`json/j-ono-source.json`), and a "data" file (`json/j-ono-data.json`).

## SOURCE RECORDS FILE
All source records are stored in a single JSON array in the `j-ono-source.json` file.  Image objects within the data file refer variously to these source records.

```
[
  { source record },
  { source record },
  ...etc.
]
```

## SOURCE RECORDS
* Each Source Record contains...
  * a "publisher_name" string (shown in J-Ono Search as publisher's copyright for associated images)
  * a "site" string (not used, just a convenience) 
  * an array of "source" objects.
* Each "source" object contains
  * a unique "id" name string
  * a "manga" title string (shown in J-Ono Search as manga title for associated images)

Example Soure Record:

```json
 {
    "publisher_name": "SHINCHOSHA",
    "site": "https://comicbunch-kai.com/",
    "sources": [
      {
        "id": "kaijuu_sdf",
        "manga": "Kaijuu Jieitai"
      },
      {
        "id": "shogun_gold_in_america",
        "manga": "Tokugawa Maizoukin wa America"
      }
    ]
  }
```

## DEFINITION RECORDS FILE
All definition records are stored in a single JSON array in the `j-ono-data.json` file.

```
[
  { definition record },
  { definition record },
  ... etc.
]
```

## DEFINITION RECORDS
* Each Definition Record contains...
  * a "literal" translation string
  * an array of "katakana" strings
  * an array of "hiragana" strings
  * an array of "definition" objects
* Each "definition" object contains...
  * a "meaning" string
  * an array of English "equivalent" strings
  * an array of "example" objects
  * a "refer" string  &nbsp;&nbsp;<sub><sup>\*\*NEW\*\*</sup></sub>
    * "refer" strings reference other definitions (for normalizing duplicate definitions)
    * the convention of a "refer" strings is `<literal>:<def num>` ("def num" is the index of the referred definition array)
    * "meaning" values from the referred definition are displayed prior to local meanings in the J-Ono search tool (as a simple concatenation)
    * "equivalent" values from the referred definition are listed prior to local equivalents in the J-Ono search tool
  * a "type" string &nbsp;&nbsp;<sub><sup>\*\*NEW\*\*</sup></sub>
    * "type" strings codify the definition classification
    * there are six possible classification types:
      * "o" = onomatopoeic (擬音語)
      * "v" = voiced/vocal (擬声語)
      * "s" = state/condition (擬態語)
      * "m" = motion/movement (擬容語)
      * "e" = emotion/feeling (擬情語)
      * "c" = meta/visual cue (記号的オノマトペ)
* Each "example" object contains...
  * a "source" string with a source id (see SOURCE RECORDS)
  * a "file" string with the filename of the image file (see IMAGE FILES)
  * a "display" string with the matching kana
  * a "contributor" string with the name of the individual that contributed the example (defaults to "Nightbug")

### Example of a Definition Records:

```json
{
  "literal": "gin",
  "katakana": [ "ギン", "ギンッ" ],
  "hiragana": [ "ぎん", "ぎんっ" ],
  "definition": [{
      "refer": "",
      "type": "e",
      "meaning": "an indication of glaring or staring",
      "equivalent": [ "fixate", "glare", "glower", "regard", "stare" ],
      "example": [{
          "source": "world_full_of_monsters",
          "file": "gin-1a",
          "display": "ギン",
          "contributor": ""
        },
        {
          "source": "dungeon_dining_room",
          "file": "gin-1b",
          "display": "ギンッ",
          "contributor": ""
        }]
    }]
}
```

### Example of a Definition Records with a Reference:

```json
{
  "literal": "ginuro",
  "katakana": [ "ギヌロ", "ギヌロォ" ],
  "hiragana": [ "ぎぬろ", "ぎぬろぉ" ],
  "definition": [{
      "refer": "gin:1",
      "type": "",
      "meaning": ", typically drawn out and menacing",
      "equivalent": [ "scowl" ],
      "example": [{
          "source": "hello_work",
          "file": "ginuro-1a",
          "display": "ギヌロォ..!",
          "contributor": ""
        }]
    }]
}
```

Note that in the J-Ono search tool, the resulting meaning of the `ginuro` definition record would be displayed as `an indication of glaring or staring, typically drawn out and menacing` and the resulting equivalents would be displayed as `fixate, glare, glower, regard, stare, scowl`.

## IMAGE FILES
* Each Image File is in a folder corresponding to its source name
* All images are 400 pixels by 400 pixels
* Naming convention: `[literal]-[unique id]`
  * Underscores are used in lieu of spaces in the literal string.
  * The `[unique id]` is merely for the convenience of human-readability - it's two or three characters long and has a number part and a letter part - the number differentiates the images by definition and the letter differentiates them by example.  So an image file with an id of `2c` would be for the third example("c") of the second definition ("2").
