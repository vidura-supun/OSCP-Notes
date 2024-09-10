
- Site was using laravel and NMAP flagged that it had .git repo

```
http-git: 
|   192.168.220.108:80/.git/
|     Git repository found!
```

- Used the tool  to extract the files

```
githacker --url http://127.0.0.1/.git/ --output-folder result
```

- In source code found below which was the admin password.

```
 DB::table('settings')->insert([
            'title' => 'Splodge',
            'filter' => '//',
            'replacement' => '',
            'password' => 'SplodgeSplodgeSplodge'

```

- After login in We see a search and replace  function

![[Pasted image 20230922234215.png]]

and this gets us a reverse shell when we comment "hey" because /e will execute the next command. This is a vulnerability in preg_replace .

- After running linpease we find the postgresql password and we login then get a reverse shell.