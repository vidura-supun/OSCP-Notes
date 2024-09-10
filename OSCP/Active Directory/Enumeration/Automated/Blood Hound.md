#enumerations #windows #activedirectory 


```bash
sudo neo4j start
```

```bash
bloodhound
```

#### Run Externally Against a DC

```bash
bloodhound-python  -d hutch.offsec -u fmcsorley -p CrabSharkJellyfish192 --zip -c all -ns 192.168.220.122
```

#### Custom Queries

Users That has sessions in the computer

```Cypher
MATCH p = (c:Computer)-[:HasSession]->(m:User) RETURN p
```

All Computers
```Cypher
MATCH (c:Computer) RETURN c
```

All Users
```Cypher
MATCH (m:User) RETURN m
```

Users and their Groups

```Cypher
MATCH p = (c:User)-[:MemberOf]->(m:Group) RETURN p
```
