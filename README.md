# jenkinsfile-yes

This repo has a Jenkinsfile.

We can change the junk-file with sed:

```
sed -i 's/a/b/gI' junk-files/big-file-da
```

* `-i` changes the file, as opposed to returning the output to stdout
* The part in single quotes `'` is our command. Slashes `/` are delimiters that separate the things we're doing, so to speak. Where, of `'s/a/b/gI'`, 
  * `s` means substitute
  * `/a/b` are the things we're substituting. In this case, we would replace `a` with `b`
* Of `/gI`, 
  * `g` means "global," or, "replace all instances of `a` that we have in the file
  * `I` means "Ignore case," or, "replace both `a` and `A` with `b`.