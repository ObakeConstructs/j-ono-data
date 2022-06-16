The data uses a very simple JSON structure in this repository.

>  
> Index File (`json/index.json`)  
> &nbsp;&nbsp;+-- Record Files (`json/x/xxx.json`)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+-- Image Files (`img/x/xxx.jpg`)  
>  

That's it.  Nothing fancy.

* INDEX FILE (standard json)
  * The Index File contain the list of all Record File filenames (sans path and extension - those are determined procedurally).
  * The Index File is sorted alphabetically, but that's just for convenience.  The search program resolves searches asynchronously, so that ordering is more-or-less irrelevant.
* RECORD FILE (standard json)
  * Each Record File contains the kana, literal translation, english equivalents, meaning (labeled `comments`), and image filenames (again, sans path and extension - the program assumes .jpg, but that can be explicitly defined to override).

        {
          "katakana": xxx,
          "hiragana": xxx,
          "literal": xxx,
          "equivalent": xxx,
          "comments": xxx,
          "examples": xxx
        }

  * Each Record File is in a folder corresponding to the first letter of its filename.
  * The Record File filenames are all based on the literal translation values.  Because we're using the literal translation this way, we sometimes fudge what constitutes a "literal translation".  For example, the entry for `fu fu` includes `fu fu fu`.  Hopefully, it's close enough that anyone looking at it can figure out that it's just more of the same jōgo.
* IMAGE FILE
  * Image files are not technically required, but we made it a point early on that we didn't want to add any definitions unless we actually had a good representational image to back it up.  
  * Each json file is in a folder corresponding to the first letter of its filename.
  * Each image is 400x400px and contains a publisher attribution statement.
