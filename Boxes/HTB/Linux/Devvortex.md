FIrst we will conduct the enumeration with rustscan to see if there are any interesting ports.

From the rustscan result we are seeing two ports of interest, 22 and 80
![[Pasted image 20231204134545.png]]

Since it is getting redirected to devvortex.htb, need to modify /etc/hosts

![[Pasted image 20231204133134.png]]

Now lets visit the website for enumeration, not a CMS and cant see any of the forms have an action tied to them which means we need to check for any hidden directories.

![[Pasted image 20231204155108.png]]

Lets run feroxbuster and see if we get any hits, nothing interesting.

Moving onto vhost enumeration with wfuff and we got a hit.
![[Pasted image 20231204192741.png]]
