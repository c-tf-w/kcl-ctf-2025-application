Flag Hunters
============

**Author**: syreal
**Tags**: `Easy` `Reverse Engineering` `picoCTF 2025`
--------

### Solve Attempt

Hints:

- This program can easily get into undefined states. Don't be shy about Ctrl-C.
- Unsanitized user input is always good, right?
- Is there any syntax that is ripe for subversion?

I don't really get the part about hitting Ctrl-C. For me it just exits the program with KeyboardInterrupt.

Looks like if it reads a RETURN at the beginning of the line in the list of strings it will jump to the number behind the RETURN (e.g. "RETURN 0" -> jumps to line 0).

You are prompted for input, which then has 'Crowd:' prepended to it using string concatenation; so putting in RETURN 0 won't get the line matched by the regex.

So you need to give it some input that causes it to be read as two lines (and put the RETURN 0 on the second line).

Poking around a bit with the debugger, it looks like ";" is "ignored" at the end of the line (e.g. song_lines[31] == 'REFRAIN;' but it checks line == 'REFRAIN'), try inputting "a;a" into the input?

> `Crowd: a`
> `a`

What. I don't really know how to explain `for line in song_lines[lip].split(';')` on first thought either. The altered line `"Crowd: a;a"` is `song_lines[11]` but the iterator reads `"Crowd: a"` then `"a"`.

So then input ";RETURN 0" when prompted, and you get the flag.

#### Flag:

`picoCTF{70637h3r_f0r3v3r_c373964d}`