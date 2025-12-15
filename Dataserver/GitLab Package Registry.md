Die folgenden Ausführungen beziehen sich auf das LabVIEW Beispielprojekt `myLvProject` .

## Upload Build

In der Git Bash folgenden Befehl ausführen:

```bash
curl --location --header "PRIVATE-TOKEN: glpat-GYqVll0IdTBLkzIa0t5MPm86MQp1OjEwCA.01.0y1amqp5e" \
     --upload-file myApp_build.zip \
     "http://192.168.178.36:8929/api/v4/projects/2/packages/generic/myLvProject/1.0.0/myApp_build.zip"
```
Der Link zum Build Release asset lautet:
http://192.168.178.36:8929/entwicklung/labview/mylvproject/-/package_files/1/download

## Upload Installer

```bash
curl --location --header "PRIVATE-TOKEN: glpat-GYqVll0IdTBLkzIa0t5MPm86MQp1OjEwCA.01.0y1amqp5e" \
     --upload-file myApp_installer.zip \
     "http://192.168.178.36:8929/api/v4/projects/2/packages/generic/myLvProject/1.0.0/myApp_installer.zip"
```
Der Link zum Installer Release asset lautet:
http://192.168.178.36:8929/entwicklung/labview/mylvproject/-/package_files/2/download

