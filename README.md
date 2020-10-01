# Script para renombrar imagenes #

- Paso 1 Abrir powershell
- Paso 2 Ingresar a la ruata dodne se tienen las imagenes
- Paso 3 Modificar el siguiente script

```powershell
$path = "\\"
$fileTypes = ".*.jpg|.*.bmp|.*.png|.*.gif|.*.tif"
$files = Get-ChildItem -Recurse | Where-Object FullName -Match ".*$path*"
$counter = 1
$dir = ""

foreach ($file in $files) {
    $name = $file.Name
    $fullname = $file.FullName
    $extension = $file.Extension

    if ($name -Match $fileTypes) {
        if ($dir -ne $file.Directory.Name) {
            $dir = $file.Directory.Name
            $counter = 1
        }


        Rename-Item $fullname "$counter$extension"

        $counter++
    }
}
```
