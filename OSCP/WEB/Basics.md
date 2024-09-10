#webapp #recon #L1
- /robots.txt - Not allowed directories  
- /sitemap.xml : Mistaken directories
- favicon : check against the [[OWASP]] database
```bash
curl example.com\favicon | md5sum
```
- Headers :  Check headers for important stuff
```bash
curl http://10.10.244.113 -v
```
