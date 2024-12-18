dirgram
=======

dirgram = directory + anagram

## Usage

```
input-of-directory-path | dirgram args...
```

## Examples

```console
$ echo /path/to/a/b/c/d/e | dirgram 3 4 5 6
a/b/c/d
$ echo /path/to/a/b/c/d/e | dirgram 3..6
a/b/c/d
$ echo /path/to/a/b/c/d/e | dirgram -- -1
e
$ echo /path/to/a/b/c/d/e | dirgram 3..-1
a/b/c/d/e
```

```console
$ echo /path/to/a/b/c/d/e | dirgram 3 6 5 4
a/d/c/b
$ echo /path/to/a/b/c/d/e | dirgram 3 3 3
a/a/a
```

```console
$ dirname /path/to/a/b/c/d/e
/path/to/a/b/c/d
$ echo /path/to/a/b/c/d/e | dirgram 1..-2
/path/to/a/b/c/d
```

```console
$ echo /path/to/a/b/c/d/e
/path/to/a/b/c/d/e
$ echo /path/to/a/b/c/d/e | dirgram 1..
/path/to/a/b/c/d/e
$ echo /path/to/a/b/c/d/e | dirgram 3..
a/b/c/d/e
$ echo /path/to/a/b/c/d/e | dirgram 3..-3
a/b/c
$ echo /path/to/a/b/c/d/e | dirgram 3..-3 | dirgram 1
a
$ echo /path/to/a/b/c/d/e | dirgram 3..-5
a
$ echo /path/to/a/b/c/d/e | dirgram 3
a
```

```console
$ echo ./local/file/1/2/3 | dirgram 1..3
./local/file/1
```

```console
$ cat dirlist.txt
/home/babarot/car/toyota/corolla/levin
/home/babarot/car/toyota/
/home/babarot/car/toyota/supra/a80
/home/babarot/car/nissan
/home/babarot/car/nissan/skyline/bnr32
/home/babarot/car/nissan/skyline/er34
/home/babarot/car/honda/city
/home/babarot/car/honda/civic/eg6
/home/babarot/car/honda/integra
/home/babarot/car/subaru
$ cat dirlist.txt | dirgram 4 | sort | uniq
honda
nissan
subaru
toyota
$ cat dirlist.txt | dirgram 5 | grep -v '^$' | sort | uniq -c
   1 city
   1 civic
   1 corolla
   1 integra
   2 skyline
   1 supra
```
