# EasyLobby, EasyCheckin/Checkout!
Allow Quick Checkin or Checkout using CustomID's from EasyLobby SVM

Project: HID - EasyLobby - Easy Check-In/Check-Out
Code Version: 1.0
Author: Benjamin Sommer
GitHub: https://github.com/remmosnimajneb
Theme Design by: HTML5 UP (HTML5UP.NET)
Licensing Information: CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/)

Note: This program has no relation to HID, EasyLobby SVM or any of it's affiliates. HID, EasyLobby SVM, and eAdvance may be trademarks of HID Global. Learn more about EasyLobby at https://www.hidglobal.com/products/software/easylobby

## Overview:
This is a quick little custom script to allow quick checkin and checkout of visitors on HID's EasyLobby SVM using CustomID's
When a visitor is registered on EasyLobby and assigned a CustomID just enter it into the input form and it will automatically find the visitor and based on their current status (PreRegistered or CheckedIn) it will check them in or out.
If the visitor is before the time it will allow override to change the time for checkin and then check them in.
If the visitor is within checkin time, it'll check them in or out
And if the Visitor is past their checkout time it'll throw and error.

## Installation:
Note: This assumes you have EasyLobby SVM installed properly and configured.

So the way this works is that it directly connects and alters the SQL Database for EasyLobby - so you need access to the local MSSQL Database on the machine it's installed on.
Meaning, if installed on another PC, you need to allow access to Port 3306 on the PC (LAN or WAN Port Forwarding works), or as we do, install this on a Local WAMP Stack, we're taking the second route.

1. Install WAMP Server - https://www.wampserver.com/en/
2. Your going to want to change Apache port to another port - as 80 or 8080 may be used by EasyLobby eAdvance - so follow this to change the port to something arbitrary (let's say 4000) https://stackoverflow.com/questions/8574332/how-to-change-port-number-for-apache-in-wamp
3. Then comes the hard part, you need to instal SQL Drivers for PHP, you need drivers for "sqlsrv" for PHP (Using PDO). It's really annoying, so I'll try to give whatever points I can, but ultimately, it can be done, just have patience, alot of it.

### Installation and Configure SQLSRV Drivers for PHP on WAMPSERVER
0. Start here to grab the drivers (if unsure, grab all of them) https://docs.microsoft.com/en-us/sql/connect/php/microsoft-php-driver-for-sql-server?view=sql-server-2017
1. Then you need to drop the extracted DLL's into "C:\wamp64\bin\php\PHP_VERSION\ext\"
2. Finally (hopefully?) you need to configure them in PHP.ini, though, WAMP has TWO PHP.ini locations, so make sure to update both: "C:\wamp64\bin\php\PHP_VERSION\php.ini" AND "C:\wamp64\bin\php\PHP_VERSION\phpForApache.ini"
3. Now in the "Dynamic Extensions" section, add all the files you just stuck in as "extension=FILENAME" - keep in mind the filename should NOT include a ".dll"
4. Finally, hopefully if it went well, just start WAMP, you may get a bunch of warnings, that MAY be ok, just keep going.
5. If this doesn't work, look around online you'll find more help.

4. Now assuming that worked.....Let's configure the Config.json file.
Insert your EasyLobby SVM SQL Username, Password and Database name.
Then you need to grab your Station ID from the SQL Server (Grab the [ID] column from dbo.Site on SSMS)
Then add an operator name into the EL_OPERATOR config (can be in words)
Then if you want a doorname, add that in, or leave as ""
5. That should be it! Create a registration and give it a shot!

P.S. make sure to lookout for JotForm to EasyLobby integration coming soon which allows for JotForm submissions to go to EasyLobby SVM registrations - allowing for a nicer UI for Program or other registrations!