# All IETF RFCs (txt)

I couldn't find an official Git repository with all IETF RFCs so I made my own.

Here's the command I used:

```sh
cd rfc
last="$(curl -sS 'https://www.rfc-editor.org/in-notes/rfc-index.txt' | rg '^[0-9]' | tail -n 1 | awk '{ print $1 }')"
seq "${last}" | parallel -j100 wget -q -c https://www.rfc-editor.org/rfc/rfc{}.txt
```

