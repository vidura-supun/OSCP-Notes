#activedirectory #enumerations 


```powershell
powershell -ep bypass
```

```powershell
Import-Module .\Sharphound.ps1
```

OR 

```powershell
. .\Sharphound.ps1
```

#### Basic Collection

```powershell
Invoke-BloodHound -CollectionMethod All -OutputDirectory C:\Users\enox -OutputPrefix "Medtech"
```
