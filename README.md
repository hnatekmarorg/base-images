# Usage

On `http://matchbox.hnatekmar.xyz:3000` edit `menu.ipxe` with 
```
#!ipxe
set countdown 6000
menu If no choice is made machine will attempt to boot via matchbox
item matchbox Autoboot via matchbox
item start Boot via netboot.xyz
choose --timeout ${countdown} --default matchbox selected || goto matchbox
goto ${selected}

:matchbox
chain http://matchbox.hnatekmar.xyz:8080/boot.ipxe || goto start
```
