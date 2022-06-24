## STRUCTURE
The data uses a very simple JSON structure in this repository.
>  
> Index File (`json/index.json`)  
> &nbsp;&nbsp;+-- Record Files (`json/x/xxx.json`)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+-- Image Files (`img/x/xxx.jpg`)  
>  

That's it.  Nothing fancy.

## INDEX FILE
* The Index File in in JSON format and contain the list of all Record File filenames (sans path and extension - those are determined procedurally).
* The Index File is sorted alphabetically, but that's just for convenience.  JSON fetch routines are asynchronous, so ordering can be inconsistent.

## RECORD FILE
* Each Record File is in JSON format and contains a literal translation string, an array of katagana, an array of hiragana, and an array of definitions.  Each definition contains a string of english equivalents, a meaning string, and an array of image filename strings.
* For Example...
```
{
  "literal": "fu",
  "hiragana": [ "ふ", "ふっ", "ふー", "ふーっ" ],
  "katakana": [ "フ", "フッ", "フー", "フーッ" ],
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
* Each Record File is in a folder corresponding to the first letter of its filename.
* The Record File filenames are all based on the literal translation values.  Because we're using the literal translation this way, we sometimes fudge what constitutes a "literal translation".  For example, the entry for `fu fu` includes `fu fu fu`.  Hopefully, it'll be close enough that anyone looking at it can figure out that it's just more of the same jōgo.
* Note that multiple definitions are grouped by number.  In the above example, there are three definitions (and three English-equivalent groups, and three examples).

## IMAGE FILE
* While, Image Files are not technically required, we made it a point early on that we didn't want to add any definitions unless we actually had a good representational image to back it up.  The [Editor Tool](https://obakeconstructs.github.io/J-Ono-Search/pages/editor) requires image filenames.
* Each Image File is in a folder corresponding to the first letter of its filename.
* All Image File images are 400 pixels by 400 pixels and contain publisher attribution statements.
* All Image File formats are JPEG (`*.jpg`), exclusively.
* All Image File filenames must be unique and carry the `.jpg` extension, but otherwise have no restrictions.
