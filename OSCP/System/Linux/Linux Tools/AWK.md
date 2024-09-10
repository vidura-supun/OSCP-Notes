#linux #command #Text_operators

##### Basic Operation
```bash
echo "hello::there::friend" | awk -F "::" '{print $1 ":" $2}' ## output is hello:there
```

###### character replace and length

```bash
awk -F "," '{gsub("{{",""); print length,$1}' ## replace {{ with nothing and get the length
```

####  Take Space as auto delimeter 

```bash
awk '{print $2,$3,$4,$5,$6,$7,$8}' ## remove commma for no space
```


