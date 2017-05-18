# esp8266

Here are my notes about using esp8266 nodeMCU.

My nodeMCUs:
![image](https://github.com/spenghui/esp8266/blob/master/mynodeMCU.jpg)

#### about firmware

when I have bought these two nodes, I found them don't work. It seems their firmwares had been damaged. So I tried to redownload a new firmware. However, all the firmwares built from relevant cloud platform proved wrong.
Finally, I found a usable firmware, which is nodemcu_float_0.9.6-dev_20150704.bin. 


#### upload customed lua script
Here is an example lua script:
```
-- init.lua
print('Setting up WIFI...')
wifi.setmode(wifi.STATION)
wifi.sta.config('360', '1234567890')
wifi.sta.connect()

tmr.alarm(1, 1000, tmr.ALARM_AUTO, function()
    if wifi.sta.getip() == nil then
        print('Waiting for IP ...')
    else
        print('IP is ' .. wifi.sta.getip())
    tmr.stop(1)
    end
end)
```
After uploading init.lua to nodeMCU through ESPlorer, the interface likes:
![image](https://github.com/spenghui/esp8266/blob/master/upload_lua_init.png)
