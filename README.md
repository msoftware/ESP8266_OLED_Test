# ESP8266 OLED Test

Based on the NodeMCU LUA script from https://github.com/nodemcu/nodemcu-firmware/blob/master/lua_examples/u8glib/u8g_graphics_test.lua I tested my new ESP8266 module with integrated OLED display.

The main difference is the port. The module uses GPIO5 for sda and GPIO4 for scl. So the initI2C looks like:

```lua
function initI2C()
   local sda = 1 -- GPIO5
   local scl = 2 -- GPIO4
   local sla = 0x3c
   i2c.setup(0, sda, scl, i2c.SLOW)
   disp = u8g.ssd1306_128x64_i2c(sla)
   print("initI2C OK")
end 
```

Everything else is unchanged.

