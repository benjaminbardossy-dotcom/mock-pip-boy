# Overview
The wrist boy is a wrist mounted device containing modules which allow it to take in readings such as the outside temperature, humidity, air pressure, air quality, user heartrate / SpO2 of the user. Readings will be displayed onto a 2.42in I2C OLED, which the player can interact with using the buttons attached. Other features include:\
-2 pairs of LED's acting as straight or perpendicular flashlights\
-A laser pointer(toggled through switches)\
-Vl53l0X module which can measure distance\
-A laser pointer for better accuracy when measuring distance\
-A small speaker + mic\
+Many other software features\
For a more indepth look at the features, see [Features](#features)\
**This design is still a WIP, and many other features are planned. See [The Future of The Wrist Boy](#the-future-of-the-wrist-boy)

# Why I Made This
I was inspired to make this after coming across this project: [The Chip-Boy](https://github.com/hungggryvic/Chip-Boy). Seeing this project, I was inspired to make my own with similar modules.

Despite similar ideas, I had envisioned a few changes to the design, including adding more "survival" based modules. I wanted this device to warn the user if there was any potential danger. To implement this, I added an SpO2 module to measure the users heartrate, an AHT20+BMP280 module for temp and air pressure, an MQ135 module for air quality, and a red LED which would flash if there was any potential danger to the user(E.x. low air quality readings from the MQ135, high temp readings from the AHT20+BMP280.).

However, the idea behind the wrist boy was always the same. I wanted a device able to take in readings from the environment around me, anytime, anywhere, with versitile highly modifiable modules which could easily be coded to fit any need. I wanted a device which could connect to wifi if needed, but run completely off grid whenever necessary as long as it has charge.

After taking into consideration what I wanted from this device, I've created the design below:

# The Design(WIP):

## Features
- **Main Functionality**
   - Custom PCB powered by an ESP32 module which serves as the heart of the device as it handles all firmware
   - Responsive user interface, which is displayed on an 2.42 inch OLED screen, and can be interacted with through the attached switches
   - Rechargable LIPO battery which can be charged through the attached TP4056 module.
   - laser which toggles on for accurate measurement when using the VL53L0X, or can alternatively be toggled through the second switch attached
   - 2 pairs of LED's which function as flashlights for the user, and are toggled through the attached switches
   - Micro SD card reader module which function as extended storage for the ESP32. For this device it stores music data, which can then be played on the attached speaker.
- **Environmental Data Gathering**
   - MAX30102 module to measure the users heatrate
   - MQ135 module to measure general air quality
   - AHT20+BMP280 to measure environmental temperature and air pressure
   - VL53L0X module for accurately measuring distance to the nearest mm
- **Audio**
   - Small speaker to play music or other audio
   - Small microphone which takes in audio and can be used to program a variety of features, such as voice activated commands
   - A piezo buzzer which adds depth to the interface by playing different frequency beeps depending on user input

## The Case
<img width="896" height="693" alt="image" src="https://github.com/user-attachments/assets/d986a54d-43c3-4538-8754-b08bb74d1f6c" />\
I designed a case to mount the PCB to, which could then slip onto the users wrist. The case features two seperate pieces which snap together to ease 3D printing and reduce support generation where possible. The PCB itself mounts to the case through the use of M2 screws. The case features 4 small holes in each corner to place M2 heat inserts into, which then mount the PCB in place by screwing in 4 M2 screws into on the 4 corners of the PCB. The case includes a small rectangular hole near the bottom, which the SpO2 module slots into, before the wires are strung through the hollow case and connected to the PCB. This allows proper heart rate readings to be read, as the module is lightly pressed into the users wrist at constant pressure. The case also includes holes for both the MQ135 and AHT20+BMP280, allowing the sensors to fit into the case and under the PCB.

## The PCB
<img width="1014" height="649" alt="image" src="https://github.com/user-attachments/assets/cd6eff4f-224c-4be9-be90-6f4aeb84834d" />\
The PCB features a 2 layer design, with a track size of 0.25mm, and an overall sizing of 67x107mm. The microcontroller used was the ESP32. which is soldered directly to the board. The OLED screen is quite large, sitting at 48x70mm, and for this reason it is mounted to female headers, allowing it to sit overtop of the ESP32 and other components. The two pairs of LED's sit off the board
## 3D View:
<img width="896" height="567" alt="image" src="https://github.com/user-attachments/assets/117c59d4-31c1-4fe9-b018-70c8b0897cfb" />\

## Wiring Schematic
<img width="3507" height="2480" alt="image" src="https://github.com/user-attachments/assets/85edcb3a-183d-456b-b924-5451f5f1c2ae" />
This wiring schematic is identical to the routing on the PCB, but shown in greater detail.

# Assembling Your Own
If you're interested in creating your own wrist boy, the simplified construction of the wrist boy is as follows:
1. Gather the necessary files(All files / folders referenced can be found at the top of this repo):
   - Download the step files found in folder labled CAD Models
   - Download the zip file containing the gerber files for the PCB labled wrist_boy_gerber.zip, found in the folder labled PCB
2. Gather the Parts
   - See the BOM below and order any parts you don't already have using the links provided
   - Go to JLCPCB and start a new order
   - Drag and drop wrist_boy_gerber.zip into the file uploader
   - Submit the order
   - Upload the step files to a 3D printing application of your choice and print the models OR upload the step files to JLCPCB's 3D printing service and add to your existing PCB order if you don't have access to a 3D printer
3. Assemble
   - Solder components to the board following the rules below and using the schematic as reference
      - make sure to solder a 4 pin female header instead of the screen to the designated OLED pins on the board
      - Do not solder the aht20+bmp280, MQ135, laser pointer, or MAX30102 directly to the board
   - Place the MAX30102 into its designated slot near the bottom of the case, placing the wires through the case
   - Superglue the connecting pieces of the 3D printed case together and let set
   - Place the MQ135 and aht20+bmp280 into their places in the case, securing with M2 screws and nuts
   - Optionally mount the laser pointer to the top of the VL53l0X
   - Use the solder gun to melt the M2 heat inserts into the case in the holes located at each corner of the case
   - Place battery into the case and secure with double sided tape
   - Place the PCB on top of the case in line with the holes
   - Using M2 screws, secure the PCB to the case
4. Firmware
   - Download the code using the provided ino file wristboy_untested.ino
   - Plug the ESP32 in, and connect to whatever device you're using to upload the code
   - Upload the code to the ESP32

## BOM
| Material      | Quantity      | Cost($CAD)     | Link          |
| ------------- | ------------- | ------------- | ------------- |
| M2 Screws | 10 | 0.21 | https://www.amazon.ca/780Pcs-Screws-Metric-Washers-Steel-Black/dp/B0D7QCS5FL?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=A3GSZ4RKHEJUDQ&th=1 |
| M2 Nuts | 6 | 0.12 | https://www.amazon.ca/780Pcs-Screws-Metric-Washers-Steel-Black/dp/B0D7QCS5FL?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=A3GSZ4RKHEJUDQ&th=1 |
| M2 Heat Inserts | 4 | 0.56 | https://www.amazon.ca/HANGLIFE-Heat-Set-Threaded-Components-Soldering/dp/B0D477R64K?th=1 |
| ESP32         | 1             |   10.99       |    https://www.amazon.ca/ELEGOO-ESP-WROOM-32-Development-Bluetooth-Microcontroller/dp/B0D8T7Z1P5?th=1           |
| Mini Step-Up Boost Converter | 1 | 3.66 | https://www.amazon.ca/CANADUINO%C2%AE-DC-DC-Step-Up-Converter-2-5-5V/dp/B09TZSGHYK/ref=asc_df_B09TZSGHYK?mcid=829455ac296e3eefbfeefdcb151b2f70&tag=googleshopc0c-20&linkCode=df0&hvadid=706724917107&hvpos=&hvnetw=g&hvrand=10632712767633782168&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9000685&hvtargid=pla-2298538843345&psc=1&hvocijid=10632712767633782168-B09TZSGHYK-&hvexpln=0&gad_source=4 |
| 3.7V 18650A 2000mAh LIPO Battery | 1 | 8.63 | https://www.aliexpress.com/item/1005010527559361.html?spm=a2g0o.order_list.order_list_main.5.46711802fXqOzT |
| 5 Way Switch | 1 | 0.88 | https://www.aliexpress.com/item/4000681560472.html?spm=a2g0o.order_list.order_list_main.44.46711802fXqOzT |
| Mini Laser Pointer | 1 | 0.66 | https://www.aliexpress.com/item/1005009410058180.html?spm=a2g0o.order_list.order_list_main.50.46711802fXqOzT |
| 2.42 inch OLED Display  | 1 | 13.58  | https://www.aliexpress.com/item/4000002579405.html?spm=a2g0o.order_list.order_list_main.61.46711802fXqOzT |
| TP4056 Lithium Battery Charger Module | 1 | 0.47 | https://www.aliexpress.com/item/32930640893.html?spm=a2g0o.order_list.order_list_main.71.46711802fXqOzT |
| VL53L0X Module | 1 | 5.69 | https://www.aliexpress.com/item/1005008798415699.html?spm=a2g0o.order_list.order_list_main.191.49da1802f3M5CC |
| MAX30102 Module | 1 | 3.07 | https://www.aliexpress.com/item/1005007015407514.html?spm=a2g0o.order_list.order_list_main.56.64ef1802V6ZYNr |
| MQ135 Module | 1 | 5.09 | https://www.aliexpress.com/item/1005009467470672.html?spm=a2g0o.order_list.order_list_main.91.46711802fXqOzT |
| AHT20+BMP280 Module | 1 | 4.89 | https://www.aliexpress.com/item/1005005982427374.html?spm=a2g0o.order_list.order_list_main.96.46711802fXqOzT |
| Mini Slide Switch 3pin | 3 | 0.37 | https://www.aliexpress.com/item/1005005633418066.html?spm=a2g0o.order_list.order_list_main.171.46711802fXqOzT |
| Micro Push Button | 2 | 0.10 | https://www.aliexpress.com/item/32815969627.html?spm=a2g0o.order_list.order_list_main.196.46711802fXqOzT |
| Led Diode, 3mm 5mm | 5 | 0.35 | https://www.aliexpress.com/item/1005007214694188.html?spm=a2g0o.order_list.order_list_main.226.46711802fXqOzT |
| Resistors | 10 | 0.06 | https://www.aliexpress.com/item/1005005855324735.html?spm=a2g0o.order_list.order_list_main.241.46711802fXqOzT |
| INMP441 Module | 1 | 5.89 | https://www.aliexpress.com/item/1005011560363321.html?spm=a2g0o.detail.0.0.128fDWY0DWY0No&mp=1&pdp_npi=6%40dis%21CAD%21CAD+11.78%21CAD+5.89%21%21CAD+5.36%21%21%21%402103128917777614208214544eb8e6%2112000055922209462%21ct%21CA%216516785883%21%211%210%21 |
| Micro SD Card Module | 1 | 3.71 | https://www.aliexpress.com/item/1005010519562186.html?spm=a2g0o.detail.0.0.6565Ol4TOl4TF1&mp=1&pdp_npi=6%40dis%21CAD%21CAD+9.08%21CAD+3.71%21%21CAD+3.38%21%21%21%402101e2b417777604375576021e62d1%2112000052676608865%21ct%21CA%216516785883%21%211%210%21 |
| MAX98357A Module | 1 | 3.07  | https://www.aliexpress.com/item/1005007068815767.html?spm=a2g0o.detail.0.0.6565Ol4TOl4TF1&mp=1&pdp_npi=6%40dis%21CAD%21CAD+3.07%21CAD+3.07%21%21CAD+2.82%21%21%21%402101e2b417777604375576021e62d1%2112000056349468594%21ct%21CA%216516785883%21%211%210%21 |
| 8Ohm 1W Speaker | 1 | 4.82 | https://www.aliexpress.com/item/1005011920753806.html?spm=a2g0o.detail.0.0.6565Ol4TOl4TF1&mp=1&pdp_npi=6%40dis%21CAD%21CAD+9.84%21CAD+4.82%21%21CAD+4.39%21%21%21%402101e2b417777604375576021e62d1%2112000057040904678%21ct%21CA%216516785883%21%211%210%21 |
| Piezo Buzzer | 1 | 0.27 | https://www.aliexpress.com/item/1005006260328559.html?spm=a2g0o.productlist.main.4.1cee40902qEetf&aem_p4p_detail=20260502153430362601419017360005695929&algo_pvid=9c8b0b99-3bbf-419b-8874-6d4fe906f763&algo_exp_id=9c8b0b99-3bbf-419b-8874-6d4fe906f763-3&pdp_ext_f=%7B%22order%22%3A%221007%22%2C%22spu_best_type%22%3A%22price%22%2C%22eval%22%3A%221%22%2C%22fromPage%22%3A%22search%22%7D&pdp_npi=6%40dis%21CAD%211.51%211.36%21%21%211.09%210.98%21%402101eede17777612699931507ec38b%2112000036509108003%21sea%21CA%216516785883%21X%211%210%21n_tag%3A-29919%3Bd%3Ab1c396d5%3Bm03_new_user%3A-29895&curPageLogUid=fZmKYKihIY1A&utparam-url=scene%3Asearch%7Cquery_from%3A%7Cx_object_id%3A1005006260328559%7C_p_origin_prod%3A&search_p4p_id=20260502153430362601419017360005695929_1 |

# The Future of The Wrist Boy
This design is not final, and I plan on refining the PCB and case alot more in the future. I plan on having a fully integrated circuit with no prebuilt modules, which woiuld save space and allow me to build a full case which encloses the hardware, and I also plan on changing and refining the code as I test the hardware. Another large modification I have planned is the addition of a 5V solar panel to charge the battery, attached to a custom PCB which allows both USB-C charging and solar charging.
