#L1  #webapp 


#### Sites

[NIP](https://nip.io) - DNS Resolution for local hosts
[OOB](https://requestbin.com/) - OOB like SSRF attacks




#### Use X& to ignore the rest of URL

![[Pasted image 20230101134251.png]]

#### Where to Look

##### When Full URL is used in a parameter in address bar
![[Pasted image 20230101134624.png]]

##### When hidden value in source
![[Pasted image 20230101134712.png]]

##### A partial URL such as just the hostname
![[Pasted image 20230101141800.png]]

##### Perhaps only the path of the URL

![[Pasted image 20230101141828.png]]


#### Bypassing Controls

##### Deny list

Attackers can bypass a Deny List by using alternative localhost references such as 0, 0.0.0.0, 0000, 127.1, 127.*.*.*, 2130706433, 017700000001 or subdomains that have a DNS record which resolves to the IP Address 127.0.0.1 such as 127.0.0.1.nip.io.

Also, in a cloud environment, it would be beneficial to block access to the IP address 169.254.169.254, which contains metadata for the deployed cloud server, including possibly sensitive information. An attacker can bypass this by registering a subdomain on their own domain with a DNS record that points to the IP Address 169.254.169.254.

  
##### Allow List

An allow list is where all requests get denied unless they appear on a list or match a particular pattern, such as a rule that an URL used in a parameter must begin with **https://website.thm.** An attacker could quickly circumvent this rule by creating a subdomain on an attacker's domain name, such as https://website.thm.attackers-domain.thm. The application logic would now allow this input and let an attacker control the internal HTTP request.

  

##### Open Redirect

If the above bypasses do not work, there is one more trick up the attacker's sleeve, the open redirect. An open redirect is an endpoint on the server where the website visitor gets automatically redirected to another website address. Take, for example, the link https://website.thm/link?url=https://tryhackme.com. This endpoint was created to record the number of times visitors have clicked on this link for advertising/marketing purposes. But imagine there was a potential SSRF vulnerability with stringent rules which only allowed URLs beginning with https://website.thm/. An attacker could utilise the above feature to redirect the internal HTTP request to a domain of the attacker's choice.

