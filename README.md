# Wrist Boy
A wrist mounted device containing modules which allow it to take in readings such as the outside temperature, humidity, air pressure, air quality, user heartrate / SpO2 of the user. Readings will be displayed onto a 2.42in I2C OLED, which the player can interact with using the buttons attached. Other features include:\
-2 pairs of LED's acting as straight or perpendicular flashlights(toggled through switches)\
-A laser pointer(toggled through switches)\
-Vl53l0X module which can measure distance\
-A laser pointer for better accuracy when measuring distance(can alternatively be toggled on/off through a switch)\
-A small speaker + mic\
+Many other software features\
In the future, I also plan on adding a 5V solar panel to charge the battery, attached to a custom PCB which allows both USB-C charging and solar charging

I was inspired to make this after coming across this video: [The Chip-Boy](https://www.instagram.com/reel/DUBcdKVFByZ/?hl=en). Seeing this video, I was inspired to make my own with similar modules. I thought it was such a cool idea, and believed I could learn more about modules and the arduino IDE by creating one of my own.

# Photos:

### The 3D model for the case I created to mount the PCB to using M2 screws. The model is comprised of two seperate parts which slot together to simplify 3D printing:
<img width="896" height="693" alt="image" src="https://github.com/user-attachments/assets/d986a54d-43c3-4538-8754-b08bb74d1f6c" />

### The PCB which will be mounted on the case:
#### 3D View:
<img width="956" height="622" alt="image" src="https://github.com/user-attachments/assets/91340fea-15ff-482a-b676-fbc31d23805c" />

#### Schematic:
<img width="981" height="614" alt="Screenshot 2026-05-02 170038" src="https://github.com/user-attachments/assets/63c93d35-d6e7-4887-87a5-3f6c5fbe6f2c" />

# BOM
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
| MQ135 Module | 1 | 5.09 | https://www.aliexpress.com/item/1005009467470672.html?spm=a2g0o.order_list.order_list_main.91.46711802fXqOzT |
| AHT20+BMP280 Module | 1 | 4.89 | https://www.aliexpress.com/item/1005005982427374.html?spm=a2g0o.order_list.order_list_main.96.46711802fXqOzT |
| Mini Slide Switch 3pin | 3 | 0.37 | https://www.aliexpress.com/item/1005005633418066.html?spm=a2g0o.order_list.order_list_main.171.46711802fXqOzT |
| Micro Push Button | 2 | 0.10 | https://www.aliexpress.com/item/32815969627.html?spm=a2g0o.order_list.order_list_main.196.46711802fXqOzT |
| Led Diode, 3mm 5mm | 5 | 0.35 | https://www.aliexpress.com/item/1005007214694188.html?spm=a2g0o.order_list.order_list_main.226.46711802fXqOzT |
| Resistors | 10 | 0.06 | https://www.aliexpress.com/item/1005005855324735.html?spm=a2g0o.order_list.order_list_main.241.46711802fXqOzT |
| INMP441 Module | 1 | 5.89 | https://www.aliexpress.com/item/1005010519562186.html?spm=a2g0o.detail.0.0.6565Ol4TOl4TF1&mp=1&pdp_npi=6%40dis%21CAD%21CAD+9.08%21CAD+3.71%21%21CAD+3.38%21%21%21%402101e2b417777604375576021e62d1%2112000052676608865%21ct%21CA%216516785883%21%211%210%21 |
| Micro SD Card Module | 1 | 3.71 | https://www.aliexpress.com/item/1005010519562186.html?spm=a2g0o.detail.0.0.6565Ol4TOl4TF1&mp=1&pdp_npi=6%40dis%21CAD%21CAD+9.08%21CAD+3.71%21%21CAD+3.38%21%21%21%402101e2b417777604375576021e62d1%2112000052676608865%21ct%21CA%216516785883%21%211%210%21 |
| MAX98357A Module | 1 | 3.07  | https://www.aliexpress.com/item/1005007068815767.html?spm=a2g0o.detail.0.0.6565Ol4TOl4TF1&mp=1&pdp_npi=6%40dis%21CAD%21CAD+3.07%21CAD+3.07%21%21CAD+2.82%21%21%21%402101e2b417777604375576021e62d1%2112000056349468594%21ct%21CA%216516785883%21%211%210%21 |
| 8Ohm 1W Speaker | 1 | 4.82 | https://www.aliexpress.com/item/1005011920753806.html?spm=a2g0o.detail.0.0.6565Ol4TOl4TF1&mp=1&pdp_npi=6%40dis%21CAD%21CAD+9.84%21CAD+4.82%21%21CAD+4.39%21%21%21%402101e2b417777604375576021e62d1%2112000057040904678%21ct%21CA%216516785883%21%211%210%21 |
