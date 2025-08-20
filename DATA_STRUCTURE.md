J-ONO keeps all its data in within two JSON files: a "sources" file (`json/j-ono-source.json`), and a "data" file (`json/j-ono-data.json`).

## SOURCES FILE
All source records are stored in a single JSON array in the `j-ono-source.json` file.  Image objects within the data file refer variously to these source records.
```
[
  { source record },
  { source record },
  ...etc.
]
```

## SOURCE RECORD
* Each Source Record contains...
  * a "publisher_name" string (shown in J-Ono Search as publisher's copyright for associated images)
  * a "site" string (not used, just a convenience) 
  * an array of "source" objects.
* Each "source" object contains
  * a unique "id" name string
  * a "manga" title string (shown in J-Ono Search as manga title for associated images)

Example Soure Record:
```
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

## DATA FILE STRUCTURE
All definition records are stored in a single JSON array in the `j-ono-data.json` file.
```
[
  { definition record },
  { definition record },
  ... etc.
]
```

## DEFINITION RECORD
* Each Definition Record contains...
  * a "literal" translation string
  * an array of "katagana" strings
  * an array of "hiragana" strings
  * an array of "definition" objects
* Each "definition" object contains...
  * either...
    * a "refer" string as a reference to another definition (for normalizing duplicate definitions)
  * or...
    * an array of english "equivalent" strings
    * a "meaning" string
  * an array of "example" objects
* Each "example" object contains...
  * a "filename" string
  * a "contributor" string
  * a "display" string
  * a "source" string

Example Definition Record:
```

{
  "literal": "an",
  "katakana": [ "アン", "アーン" ],
  "hiragana": [ "あん", "あーん" ],
  "definition": [{
    "refer": "",
    "equivalent": [ "aah", "ahh", "mah", "wah" ],
    "meaning": "a wide open mouth, as preparing to eat something",
    "example": [{
      "file": "an-1a",
      "contributor": "",
      "display": "あーん",
      "source": "otherworld_material_collector"
    }]
  }]
}

```

## IMAGE FILE
* Each Image File is in a folder corresponding to its source name
* All images are 400 pixels by 400 pixels
* All image formats are exclusively JPEG (`*.jpg`), for the time being
* Naming convention: `[literal]-[unique id]`
  * Underscores are used in lieu of spaces in the literal string.
  * The `[unique id]` is merely for the convenience of human-readability - it's two or three characters long and has a number part and a letter part - the number differentiates the images by definition and the letter differentiates them by example.  So an image file with an id of `2c` would be for the third example("c") of the second definition ("2").
