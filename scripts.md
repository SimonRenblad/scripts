### select a python process id and kill it
```
ps -o "%c|%p" --no-headers \
| tr -d " " \
| awk -F '|' '/python/{ print $2 }' \
| fzf \
| xargs kill -9
```

### search any local process and kill it
```
ps -o. "%c,%p" --no-headers | tr -d " " | fzf | sed "s/.*,//" | xargs kill -9
```

### search command in history and run it
```
history | fzf | sed 's/^ *[0-9]* *//' | bash
```

### monkeytype style typing test in a pipeline
```bash
echo (shuf -i 1-1000 -n 5) (shuf 1000-most-common-words.txt -n 20 | punctuate -) | tr ' ' '\n' | ttyper -
```
needs `github:SimonRenblad/punctuate`. Can use other terminal typing tests like `tt`.
