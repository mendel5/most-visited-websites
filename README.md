# most-visited-websites
How to get a list of the most visited websites when using Mozilla Firefox

## Code

- Copy the full browser history and paste it to a .txt file

```
cat FILE | cut -d'/' -f3 | sort | uniq -cd | sort -nr > ./ranked-websites-no-protocol.txt
# Domain names only
# Example:
# https://en.wikipedia.org/wiki/Linux
# is returned as
# en.wikipedia.org

cat FILE | cut -d'/' -f1,2,3 | sort | uniq -cd | sort -nr > ./ranked-websites-with-protocol.txt
# Domain names including protocol
# Example:
# https://en.wikipedia.org/wiki/Linux
# is returned as
# https://en.wikipedia.org
```

```
sort random-001.txt | uniq -cd | sort -nr

cat websites-001.txt | cut -d'/' -f1,2,3
prints websites with protocol (e.g. https)

--

cat websites-001.txt | awk -F[/:] '{print $4}'
prints websites without protocol (e.g. https)

cat websites-001.txt | cut -d'/' -f3
prints websites without protocol (e.g. https)

```

## Links
- https://www.ghacks.net/2020/06/08/how-to-display-most-visited-pages-in-firefoxs-address-bar/
- https://support.mozilla.org/en-US/questions/1195457
- https://stackoverflow.com/questions/2497215/how-to-extract-domain-name-from-url
- https://www.cyberciti.biz/faq/get-extract-domain-name-from-url-in-linux-unix-bash/
- https://stackoverflow.com/questions/6712437/find-duplicate-lines-in-a-file-and-count-how-many-time-each-line-was-duplicated
