Big Zip
===

**Author**: LT 'syreal' Jones
**Tags**: `Easy` `General Skills` `picoGym Exclusive`

---

### Solve Attempt

Hint:

- Can grep be instructed to look at every file in a directory and its subdirectories?

It can:

`$ man grep`

> -r, --recursive
              Read  all  files  under  each  directory, recursively, following
              symbolic links only if they are on the command line.  Note  that
              if   no  file  operand  is  given,  grep  searches  the  working
              directory.  This is equivalent to the -d recurse option.

`$ grep picoCTF -r big-zip-files`
>`big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}`

#### Flag:

`picoCTF{gr3p_15_m4g1c_ef8790dc}`
