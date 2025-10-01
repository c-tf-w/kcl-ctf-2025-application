CanYouSee
===

**Author**: Mubarak Mikail
**Tags**: `Easy` `Forensics` `picoCTF 2024` `browser_webshell_solvable`
---

### Solve Attempt

Hint:

- How can you view the information about the picture?
- If something isn't in the expected form, maybe it deserves attention?

I suspect the flag is hidden in the metadata of the picture.

Opening the picture in an image viewer of your choice (I used [Pix](https://github.com/linuxmint/pix)), you can see some embedded XMP metadata:

|attributionURL|cGljb0NURntNRTc0RDQ3QV9ISUREM05fYTZkZjhkYjh9Cg==|
|---|---|

Putting `cGljb0NURntNRTc0RDQ3QV9ISUREM05fYTZkZjhkYjh9Cg==` into CyberChef from base64 default settings gives the flag.

#### Flag:

`picoCTF{ME74D47A_HIDD3N_a6df8db8}`
