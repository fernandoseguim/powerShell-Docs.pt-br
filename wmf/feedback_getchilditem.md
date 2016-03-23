# Get-ChildItem contém o parâmetro -Depth
**Get-ChildItem** agora tem um parâmetro **–Depth** que é usado com **–Recurse** para limitar a recursão:

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:33 PM Depth1
<!--HONumber=Mar16_HO2-->
