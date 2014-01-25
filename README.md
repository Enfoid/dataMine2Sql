dataMine2Sql
============

hard-extension to the DataMine Plugin to write and read collected data into a (my)Sql Database for re-use and backup

Required things:
- Micasaverde / Vera Controller
- installed Datamine Plugin http://code.mios.com/trac/mios_datamine
- a mysql Server
- a web-server with php running
- coffee, 230 Volts

Installation:
- add database user

- set up database

- checkout the repro to your webserver

- Download from your Vera Controller the file 'L_DataMine1.lua'
  [ APPS - Develop Apps - Luup Files - L_DataMine1.lua - Download]
- open file and add the following lines

- somewhere in the configuration section
local remoteUrl = "http://hostofyourserver/datamine/insert.php?"

- search for "outf:write(json.encode(newEvt)"
  insert the following line right below
luup.inet.wget(remoteUrl .. 'json=' .. urlEncode(json.encode(newEvt)) , 5)

- save file nd upload it back to your vera (check Reload)


ToDo:
- autopatch lua files
- create vera config (device variables ? (hardcoded for now))
- check on existing tables and build query based on fields do existing or not

Changelog:
- Collection of basic structural ideas.
