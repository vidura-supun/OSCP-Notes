#linux #command #Text_operators 

##### Replace a String

```bash
echo "I need to try hard" | sed 's/hard/harder/'
```

###### Replace the other Stuff

```bash
echo "I need to try hard" | sed -z 's/\n/""/g;s/.$/\n' ##and replace the last character with a new line
```
