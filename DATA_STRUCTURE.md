## STRUCTURE
All definition records are stored in a single JSON array in the `json/all.json` file.
> [  
>     { definition record }  
>     { definition record }  
>     ... etc.  
> ]

That's it.  Nothing fancy.

## DEFINITION RECORD
* Each Definition Record contains a "literal" translation string, an array of "katagana" strings, an array of "hiragana" strings, and an array of "definition" objects.  Each definition object contains an english "equivalent" string, a "meaning" string, and an array of "example" image filename strings.

Like this...
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
* While, Image Files are not technically required, we made it a point early on that we didn't want to add any definitions unless we actually had a good representational image to back it up.
* Each Image File is in a folder corresponding to the first letter of its filename.
* All Image File images are 400 pixels by 400 pixels and contain publisher attribution statements.
* All Image File formats are JPEG (`*.jpg`), exclusively.
* All Image File filenames must be unique and carry the `.jpg` extension, but otherwise have no restrictions.

## OTHER FILES
There is an index.json file and some folders with individual definition record files.  These are not used by the Search program, only `json/all.json` is actually used.  These files are deprecated, but necessary for some automation tasks.
