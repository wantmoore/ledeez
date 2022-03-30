# ledeez
This is the beginnings of a project to build a barebones, low-cost, ESP32-based board to control addressable LEDs.

Boards are [now available for purchase](https://ledeez.square.site/) if that's your thing.

# The Story
Since early-November 2021, I've invested about 60 hours designing my addressable LED development board. I ordered the initial v0.1 prototype from JLC PCB in late November and as soon as the order was submitted, I immediately went to work on refining the idea for v0.2.

That first batch landed on my doorstep around the first week of December, and that's when I quickly realized I had a LOT to learn about power management. The low dropout voltage regulators (LDOs) I chose to get 5v and 3.3v from 12v on that first design were a very bad choice. I went back to work - researching designs and talking with people smarter than me and landed on implementing a buck converter design. This meant adding a lot of additional components. The Bill of Materials (BOM) on v0.1 was around 12 components and a minimalistic buck converter circuit was going to add about that same number of parts. A goal from the very beginning of my endeavor was to make this board super low-cost. I studied a few reference designs and every time I sat down to draw the schematic and place the parts on the PCB, I would discover there was a chip shortage or the buck converter chip alone was $2-3 each. More research.

After a few cycles of this, I ran across the XLSEMI XL1509 - less than $0.30 per chip and only required four additional external components (input cap, inductor, schottky diode and output cap). Within a few hours, LEDeez v0.3 was done. The buck converter circuit replaced the original 12->5 LDO and I also removed the 12->3.3 LDO and replaced it with a more common AMS1117-3.3.

This is where we are today. A list of hopes and dreams for future revisions can be found below and if you're interested in pitching in, feel free to [Buy Me a Coffee](https://www.buymeacoffee.com/wantmoore) or three.

## Schematic
![image](https://user-images.githubusercontent.com/1414156/154154673-4e9ffe78-b425-4473-8976-f4717318814b.png)

## PCB Render
![image](https://user-images.githubusercontent.com/1414156/154154617-0f76bc32-188b-4f18-8ca2-39bf6148648d.png)

## 3D Render
![image](https://user-images.githubusercontent.com/1414156/154155044-f247e468-d465-41a6-b2f2-7e03ecc58163.png)
![image](https://user-images.githubusercontent.com/1414156/154155419-26697523-6a3b-43e9-8fdc-1388fd92de59.png)
![image](https://user-images.githubusercontent.com/1414156/154155287-8e6ef53e-0229-49d3-972a-1e6fe4199184.png)

## Bill of Materials (BOM)
2022-02-15: This current BOM is based on 0.3 and needs updated for a few modified components in v1.0
All components sourced from JLCPCB and/or LCSC
|Name|Designator|Quantity|Manufacturer Part|Manufacturer|LCSC Part #|
|:--|:--|:--|:--|:--|:--|
|TS-1101-C-W|SW1|1|TS-1101-C-W|XKB Connectivity|C318938|
|470uF|CIN|1|VEJ471M1ETR-1010|LELON|C176672|
|SN74AHCT125DR|U5|1|SN74AHCT125DR|TI|C7xxx|
|ESP32-WROOM-32E(16MB)|U3|1|ESP32-WROOM-32E(16MB)|Espressif Systems|Cxxxxx|
|PA001-2P|CN1,CN2,CN3,CN4|4|PA001-2P|HIWA|C128027|
|HDR-M-2.54_1x8|J1|1|||C190820|
|HDR-M-2.54_2x6|J2|1|||C124388|
|HDR-M-2.54_1x2|J3|1|||C124375|
|XL1509-5.0E1|U1|1|XL1509-5.0E1|XLSEMI|C61063|
|220uF|COUT|1|ERZ1HM181F16OT|AISHI|C10xxxx|
|5.1|R3|1|0805W8F510KT5E|UniOhm|C17724|
|1uF|C1|1|CL05A105KA5NQNC|SAMSUNG|C52923|
|SS32_C65002|D1|1|SS32|MDD|C65002|
|68uH|L1|1|SMMS1040-680MT|ShunXiang Connaught Elec|C286354|
|AMS1117-3.3|U4|1|AMS1117-3.3|AMS|C6186|
|AC0805FR-7W51RL|R1,R2|2|AC0805FR-7W51RL|YAGEO|C727996|
|10uF|C2|1|CA45-B-25V-10uF-K|CEC|C128259|

PCB Revision v1.0 as of 2022-02-15

## Future Dreams
*Build IO shield (digital mic, relay for power output, status ws2811 pixel)
