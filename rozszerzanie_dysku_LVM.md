**Tagi: [[uczen]] [[Informatyk]] [[Linux]] [[Homelab]]**
**Data: 11-07-2026**

na poczatku uzywasz lvm, wiec ubuntu daje mu tylko 100GB. jak to zmienic?

sprawdzasz jak nazywa sie przestrzen uzywajac `df -h`

zobaczysz liste dyskow. poszukaj dysku ktory chcesz edytowac i w kolumnie "Mounted on" ma sam `/`.

no i wtedy dajesz komende ktora daje mu pozostala wolna ilsoc wysku (zmien nazwe jezeli to z pustym `/` nazywa sie inaczej)
```
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
```

poinformuj system plikow ze masz wiecej miejsca

```
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

