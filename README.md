# most-visited-websites
How to get a list of the most visited websites when using Mozilla Firefox

## Code

- Open the browsing history in Mozilla Firefox by pressing `Ctrl` + `Shift` + `H`
- Copy the full history from Mozilla Firefox and paste it to a .txt file, e.g. `my_history.txt`
- Use one of the following commands on a GNU/Linux system:

```
cat my_history.txt | cut -d'/' -f3 | sort | uniq -cd | sort -nr > ./ranked-websites-no-protocol.txt
# Returns the domain names without their protocol
# Example:
# https://en.wikipedia.org/wiki/Linux
# is returned as
# en.wikipedia.org
```

```
cat my_history.txt | cut -d'/' -f1,2,3 | sort | uniq -cd | sort -nr > ./ranked-websites-with-protocol.txt
# Returns the domain names with their protocol
# Example:
# https://en.wikipedia.org/wiki/Linux
# is returned as
# https://en.wikipedia.org
```

```
cat my_history.txt | cut -d'/' -f3 | grep -ive "www\." | grep -e "\..*\." | sort | uniq -cd | sort -nr
# Returns the domain names (without their protocol) that have a subdomain and this subdomain is not "www."
# Example:
# https://www.wikipedia.org
# is not returned because its subdomain is "www."
# https://en.wikipedia.org/wiki/Linux
# is returned as "en.wikipedia.org" because its subdomain is "en."
```

## Links
- https://www.ghacks.net/2020/06/08/how-to-display-most-visited-pages-in-firefoxs-address-bar/
- https://support.mozilla.org/en-US/questions/1195457
- https://stackoverflow.com/questions/2497215/how-to-extract-domain-name-from-url
- https://www.cyberciti.biz/faq/get-extract-domain-name-from-url-in-linux-unix-bash/
- https://stackoverflow.com/questions/6712437/find-duplicate-lines-in-a-file-and-count-how-many-time-each-line-was-duplicated
