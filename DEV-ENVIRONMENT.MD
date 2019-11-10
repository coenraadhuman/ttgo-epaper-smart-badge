https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json

"ESP32 Dev Module"


https://www.tindie.com/products/ttgo/lilygor-ttgo-t5-213-inch-e-paper-new-driver-chip/
https://youtu.be/GjwE1Eq4o6c


https://www.instructables.com/id/Tide-and-Weather-Clock/

Battery Local 3.7V 500mAh
https://www.robotics.org.za/DTP652535

@ R 170

Room for battery ?

This is the correct ?
https://www.thingiverse.com/thing:3462483

This is one fir 4 button version
https://www.thingiverse.com/thing:3487291


Other
https://www.thingiverse.com/thing:3338364



https://www.tedizen.com/ttgo-tbadge-getting-started-tutorial/

POSTED ON OCTOBER 16, 2019 BY SARATH KUMAR

16
Oct
TTGO T-Badge is one of the Lilygo Boards. It has wide range of boards that are very useful for development purposes as it integrates the necessary functionalities. The T-Badge board comes with E-Ink Displays. When I getting started I have only limited resources and find trouble in making it work. I’m going to share you the issues I have faced and how I resolved it to make it work.

GitHub Repository: https://github.com/lewisxhe/TTGO-EPaper-Series
Step 1: The first step is to install the ESP32 Boards in our Arduino IDE if it is not installed already. To do that go to Files>Preferences. In the additional Boards Manager URLs, we need to add the ESP32 Boards link to install all ESP32 Boards. It is a simple json file containing the board types and it will grab the necessary files that we need to install.

So simply paste the URL and click OK.
https://dl.espressif.com/dl/package_esp32_index.json
If you have already ESP8266 URL or ATTiny, etc. You can simply put a comma(,) between the URLs and click OK.
https://dl.espressif.com/dl/package_esp32_index.json, http://arduino.esp8266.com/stable/package_esp8266com_index.json
Step 2: Now go to Tools>Boards>Boards Manager. Search ESP32 and install the boards. After installation, you can able to see ESP32 related boards on the boards menu.


Step 3: Install a webserver resource tool to our IDE. It is a simple Java based tool to upload our image/data files to ESP32 Memory using SPIFFS.
So to install it, first download the ESP32FS-vX.zip file and Extract the contents to the path <C:\Users\Your User Name\Documents\Arduino\tools>
Now you can able to see a new menu in Ardunio IDE, Tools -> ESP32 Sketch data Upload.

Note: Inside the folder of Arduino File (.ino), there should be folder called ‘data’. In that folder we need to keep the files to be uploaded to ESP32. Here we will be keeping, HTML Files, BMP, CSS,etc in this folder to make it as a mini server.
Now if we open the .ino file and choose Tools -> ESP32 Sketch data Upload, the files in the data folder will be uploaded to the ESP32’s memory.
Now we just need to upload the .ino file to use ESP Programs. The data files will already in ESP Memory and will not erase when we upload code.
Before uploading the code, we need to install the dependency files, that is our library files. Here we need to install the following libraries,
Button2
GxEPD
Adafruit-GFX-Library
AsyncTCP
ESPAsyncWebServer
ArduinoJson
ESP8266Audio
CAUTION: The Arduino Library Manager installs the ArduinoJSON version 6 by default. In here using version 5 is recommended because version 6 is still in beta stage. Please select 5.13.2 version to install on the release page.

Now we are setup almost everything. Let’s gets started with the Arduino Coding part.
There are two ways we can use the example file,
AP Mode (ESP will act as Hotspot)
Station Mode (Accessing ESP32 via an existing network with network credentials).
We are going to use station mode example as it will be easier for beginners. The given code is for Station mode. You need to modify few things in the code.
Have a look at your Display model and Size. The model which I use is TTGO Epaper 2.13 inch B/W. The version is T5_V2.3_2.13 (2.13 mentions the display size here).

Change 1:
Now navigate to C:\Users\YourUsername\Documents\Arduino\libraries\TTGO-EPaper-Series-master folder. Open the ‘board_def.h’ file. At the start of the file, we will have our board versions. We need to change the version of our board from 0 to 1 and keep 0 for all other boards. I have
#define TTGO_T5_1_2 0
#define TTGO_T5_2_0 0
#define TTGO_T5_2_1 0
#define TTGO_T5_2_2 0
#define TTGO_T5_2_3 1 //Changed to 1 for my board version
#define TTGO_T5_2_4 0
#define TTGO_T5_2_8 0 //! Silk screen marking T5_V28_27
Now save and exit the file.
Open the example file given. By default, all the header file are commented. We need to uncomment the header file for our board. But as it is in development they included a new header file type for my display time that is not available in the old code. So I need to include the following header file,
#include <GxGDE0213B72B/GxGDE0213B72B.h>      // 2.13" b/w
Change 2: Set Your Wi-Fi Credentials here
#define WIFI_SSID "Your SSID"
#define WIFI_PASSWORD "Your Password"
Change 3: We are not using AP Mode. So the following line should be removed or ‘uncomment it’.
//#define USE_AP_MODE
That’s it. We can now upload the code. Select the COM Port and Choose the Board Type as ‘ESP32 Dev Module’ or TTGO T-Beam. Upload the code.
Code

Now if you press the button 2(IO39), you can able to toggle the displays. If you want to change the contents, open serial monitor and wait for few seconds to see the IP Address. Copy and paste it in a browser and hit enter.
You can able to see a form. Type in your details and submit. In the telephone field, other than this number ‘18503000000’ all other number shows malformed number. I have checked the index.html file, there is some regular expression written. Have to check what it does. For now use that number and hit ‘commit’. You can now able to see the details on EPaper Display that you are entered on the form.


https://www.onlineconverter.com/png-to-bmp
https://createqrcode.appspot.com/



