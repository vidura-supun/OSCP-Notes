#webapp #bruteforce #tool 


### Basic 

```bash
feroxbuster -u http://192.168.186.151 -r -x php -C 404
```

### Basic Auth crawling

- base64 encoded **username:password**

```bash
feroxbuster -u http://192.168.186.220 -r -x docx -x odt -x pdf -C 404 -H "Authorization: Basic c2t5bGFyazpVc2VyK2RjR3Zmd1RialZbXQ=="
```