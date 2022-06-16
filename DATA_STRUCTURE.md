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
* The Index File is sorted alphabetically and grouped by first letter, but that's just for convenience.  JSON fetch routines are asynchronous, so any ordering is more-or-less irrelevant.

## RECORD FILE
* Each Record File is in JSON format and contains the kana, literal translation, english equivalents, meaning (labeled `comments`), and image filenames (again, sans path and extension - the program assumes .jpg, but that can be explicitly defined to override).
* For Example...
```
{
  "katakana": [ "バ", "バッ" ],
  "hiragana": [ "ば", "ばっ" ],
  "literal": "ba",
  "equivalent": [ "1 - about-face, pivot, spin, turn, whirl", "2 - fwip, fwit, pop, snap", "3 - bam, bang, crash, slam, slap, smack, thump, thud, thunk, whack, wham, whap, whomp" ],
  "comments": [ "1 - turning around suddenly", "2 - a sudden and/or fast movement", "3 - a sudden and loud impact" ],
  "examples": [ "ba-1", "ba-2", "ba-3" ]
}
```
* Each Record File is in a folder corresponding to the first letter of its filename.
* The Record File filenames are all based on the literal translation values.  Because we're using the literal translation this way, we sometimes fudge what constitutes a "literal translation".  For example, the entry for `fu fu` includes `fu fu fu`.  Hopefully, it'll be close enough that anyone looking at it can figure out that it's just more of the same jōgo.
* Note that multiple definitions are grouped by number.  In the above example, there are three definitions (and three English-equivalent groups, and three examples).

## IMAGE FILE
* Image Files are not technically required, but we made it a point early on that we didn't want to add any definitions unless we actually had a good representational image to back it up.  
* Each Imgage File is in a folder corresponding to the first letter of its filename.
* All Image File images are 400 pixels by 400 pixels and contain a publisher attribution statement.
* All Image File filenames end with a dash-number (i.e. `ba-1.jpg`).  The number corresponds to the definition group and is used by the J-ONO Search program to display the link to the image.
