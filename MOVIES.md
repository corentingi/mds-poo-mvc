```bash
awk -F '\t' '{ if ($2!="movie" && $2!="short") print }' /Users/cgitton/Downloads/IMDB/title.basics.tsv > /tmp/title.basics.filtered.tsv
```


