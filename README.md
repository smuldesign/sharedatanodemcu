# sharedatanodemcu

A manual how to connect data from 1 nodemcu with other nodemcu's with Wifi and Adafruit.



## Hardware Required

• 2x* nodemcu  
• 1x LDR / photoresistor  
• 10k ohm resistor  
• Breadboard  
• Micro USB cable  
• Connecting Wires  

*You can have multiple nodemcu's but for this example I use just 2.



### Software Required

```
Arduino IDE (with ESP8266 Library installed)
```

[Arduino IDE](https://www.arduino.cc/en/main/software)
[ESP8266 Library](http://arduino.esp8266.com/stable/package_esp8266com_index.json)



### Prerequisites

What things you need to install the software and how to install them:
```
For this project you will need an adafruit io account.
https://io.adafruit.com
```

[Adafruit](https://io.adafruit.com)

```
Get your AIO Key (right upper corner on adafruitio dashboard).
```
```
Get you Wifi SSID and PASSWORD ready.
```


### Arduino libaries

Open up arduino go to Sketch --> Include libary --> Manage Libaries
(Shift + CMD + I)

And search for the following libaries:

```
Adafruit IO Arduino by:Adafruit
(latest version)
```


### Adafruit Feed
Go to you dashboard
Create a nieuw feed and name it "counter"


### Coding Time

#### Setup Config.h

Open File --> Exampels --> Adafruit IO Arduino --> adafruit_00_publish

In the file navigate to the second tab named: config.h

Change this section to your own information form adafruit
```C
#define IO_USERNAME   "your_username"
#define IO_KEY        "your_key"
```

change this information to your own WIFI information
```C
#define WIFI_SSID   "your_ssid"
#define WIFI_PASS   "your_pass"
}
```
You can delete the FONA and ETHERNET sections because we work with WIFI.
You should left something with this of you are on wifi:
```C
#define IO_USERNAME   "your_username"
#define IO_KEY        "your_key"

#define WIFI_SSID   "your_ssid"
#define WIFI_PASS   "your_pass"

#include "AdafruitIO_WiFi.h"

#if defined(USE_AIRLIFT) || defined(ADAFRUIT_METRO_M4_AIRLIFT_LITE)
  #if !defined(SPIWIFI_SS) // if the wifi definition isnt in the board variant
    #define SPIWIFI SPI
    #define SPIWIFI_SS 10  // Chip select pin
    #define NINA_ACK 9    // a.k.a BUSY or READY pin
    #define NINA_RESETN 6 // Reset pin
    #define NINA_GPIO0 -1 // Not connected
  #endif
  AdafruitIO_WiFi io(IO_USERNAME, IO_KEY, WIFI_SSID, WIFI_PASS, SPIWIFI_SS, NINA_ACK, NINA_RESETN, NINA_GPIO0, &SPIWIFI);
#else
  AdafruitIO_WiFi io(IO_USERNAME, IO_KEY, WIFI_SSID, WIFI_PASS);
#endif
}
```

#### Sent data to Adafruit

Navigate back to the first tab Adafruitio_00_publish.
You can leave everything there and upload it to you nodemcu to test.

If you did the previouse steps correct you should see this in the serial monitor:

Inline-style: 
![alt text](https://github.com/smuldesign/sharedatanodemcu/blob/master/images/serialmonitor.png "Logo Title Text 1")
`Note: make sure your serial monitor is on 115200`


check your adafruit feed, you should see something like this.
Inline-style: 
![alt text](https://github.com/smuldesign/sharedatanodemcu/blob/master/images/adafruit.png "Logo Title Text 1")


## Authors

* **Marc Heemskerk** - [Marc Heemskerk](https://github.com/X-Track)
