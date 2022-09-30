# Peter Bulthaup Archiv – Prüfsummen

MD5-Prüfsummen der Master-Dateien. Mithilfe des Total Commander (Windows) oder mit `md5sum` (Linux) kann die Datenintegrität von Kopien des Archivs überprüft werden.

Schema:

`NNN_win_tc.md5` -- Prüfsummen für Windows/Total Commander  
`NNN_linux.md5` -- Prüfsummen für Linux/md5sum

Die enthaltenen Pfade sind relativ zum jeweiligen Teil NNN.

Die Prüfsummen wurden im September 2022 erstellt. Die Quelle waren die externen Festplatten, die als "Archiv Master Backup" gelabelt sind. Die dort enthaltenen Daten wurden 2013 geschrieben.

## Checks

### Windows

TODO

### Linux

Die Pfadangeben der Prüfsummen sind relativ, zum Beispiel

~~~
9c267da4fd0ea6b120a81da5d7a4dcf9  EXA/EXA-029/EXA-029_175.tif
~~~

Für die Überprüfung muss daher in das Verzeichnis gewechselt werden, in dem sich _EXA_ befindet. Die Prüfsummendatei kann an beliebiger Stelle liegen und muss dann entsprechend referenziert werden:

~~~
$ md5sum -c /absoluter/pfad/zu/pba-checksums/EXA_linux.md5 > EXA_ergebnis.txt
~~~

Hier wird das Ergebnis der Checks in die Datei *EXA_ergebnis.txt* umgeleitet.

War der Test für alle Dateien erfolgreich? – `md5sum` gibt das Ergebnis für jede Datei nach einem Doppelpunkt aus:

~~~
...
EXA/EXA-001/EXA-001_006.tif: OK
EXA/EXA-001/EXA-001_007.tif: OK
EXA/EXA-001/EXA-001_008.tif: OK
...
~~~

Wir trennen die "OK" ab und sortieren sie mit der Option `-u` für unique.

~~~
cat EXA_ergebnis.txt | cut -d ':' -f2 | sort -u
~~~

Wenn alle Zeilen mit "OK" enden, erzeugt dies ein einziges OK als Output. Sollten einige Zeilen nicht okay sein, stehen dort auch andere Worte, z. B. "GESCHEITERT".


## Log: durchgeführte Checks

| Wann | Was | Datenträger | Ergebnis |Anmerkung|
|------|-----|-------------|----------|---------|
|20.09.2022|DIV, MAP, KAS, VNS|neue Archivplatte 2022<br> WD Elements, 6TB|OK|verifiziert Kopie von<br>Archiv Master Backup 3 und 4|
|30.09.2022|EXA, RBL|neue Archivplatte 2022<br>WD Elements, 6TB|OK|verifiziert Kopie von<br>Archiv Master Backup 2|


