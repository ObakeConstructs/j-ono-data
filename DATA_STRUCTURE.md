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
  * an array of "katagana" strings
  * an array of "hiragana" strings
  * an array of "definition" objects
* Each "definition" object contains...
  * a "refer" string as a reference to another definition (for normalizing duplicate definitions)
    * the convention of a "refer" strings is `<literal>:<def num>`, where "def num" is the array index of the referred definition
    * a non-blank "refer" string will supercede all "meaning" and "equivalent" values in the Search tool.
  * a "meaning" string
  * an array of english "equivalent" strings
  * an array of "example" objects
* Each "example" object contains...
  * a "source" string with a source id (see SOURCE RECORDS)
  * a "file" string with the filename of the image file (see IMAGE FILES)
  * a "display" string with the matching kana
  * a "contributor" string with the name of the individual that contributed the example (defaults to "Nightbug")

Examples of Definition Records:

```json
{
  "literal": "baki",
  "katakana": [ "バキ", "バキッ" ],
  "hiragana": [ "ばき", "ばきっ" ],
  "definition": [{
      "refer": "",
      "meaning": "a sound of something cracking or breaking",
      "equivalent": [ "crack", "crash", "pop", "shatter", "smash", "snap" ],
      "example": [{
          "source": "hanako_24th_ward",
          "file": "baki-1a",
          "display": "バキッ",
          "contributor": ""
        }]
    }]
}
```

```json
{
  "literal": "bakin",
  "katakana": [ "バキン", "バキンッ" ],
  "hiragana": [ "ばきん", "ばきんっ" ],
  "definition": [ {
      "refer": "baki:1",
      "meaning": "",
      "equivalent": [""],
      "example": [{
          "source": "abandoned_reincarnation_sage",
          "file": "bakin-1a",
          "display": "バキンッ",
          "contributor": ""
        }]
    }]
}
```

## IMAGE FILES
* Each Image File is in a folder corresponding to its source name
* All images are 400 pixels by 400 pixels
* All image formats are exclusively JPEG (`*.jpg`), for the time being
* Naming convention: `[literal]-[unique id]`
  * Underscores are used in lieu of spaces in the literal string.
  * The `[unique id]` is merely for the convenience of human-readability - it's two or three characters long and has a number part and a letter part - the number differentiates the images by definition and the letter differentiates them by example.  So an image file with an id of `2c` would be for the third example("c") of the second definition ("2").
