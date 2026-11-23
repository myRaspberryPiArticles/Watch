# Watch
An analog IC chip watch powered with a LiPo and outputs in digital time on segment displays! Analog, or digital!? Thanks to Hackclub Forge and PCBWay for making this possible! Go check them out and make cool things like this as well! Here is more about it!:

## Pictures - _a picture tells 1000 words_
<p align="center">
  <img src="https://github.com/user-attachments/assets/c7c05229-2e91-4b06-a030-21971276b2e8" width="220" alt="Screenshot 2026-11-21 at 13 44 47" />
  <img src="https://github.com/user-attachments/assets/652c222f-1a9c-45a7-8d18-9b70907ee796" width="220" alt="Screenshot 2026-11-21 at 13 40 49" />
  <img src="https://github.com/user-attachments/assets/7b60ccdc-eb65-452c-acd6-e70d0118c34d" width="140" alt="Screenshot 2026-11-21 at 13 37 32" />
  <img src="https://github.com/user-attachments/assets/78ecca67-8a6a-4a20-b5d0-47ed2de687f8" width="240" alt="Screenshot 2026-11-21 at 13 31 53" />
  <img src="https://github.com/user-attachments/assets/d7b965fe-22ab-45bd-89fd-215f70a9a9ff" width="220" alt="Screenshot 2026-11-21 at 13 25 24" />
  <img src="https://github.com/user-attachments/assets/0c972868-2f1c-442c-98f2-109ab41068ee" width="240" alt="Screenshot 2026-11-23 at 17 45 16" />
  <img src="https://github.com/user-attachments/assets/aab97d77-3123-49d0-a7dd-2a86989712fc" width="280" alt="Screenshot 2026-11-23 at 17 45 00" />
</p>

## What does is it do? 
This watch is my V1 of a fully analog circuit, and by far the most complex PCB I have made. The aim is for it to be able to keep track of time precisely and then output it to four 7-segment displays, for the user to see when they have clicked the show time button. Usually, a watch would show the time constantly, but because  of battery constraints, I had to adapt to make it only show when the user wanted it to be seen. The 7-segment displays automatically wrap around after hitting 23:59, as it is the 24 hour clock's largest possible time. All the details will be explained in the 'How does it work' section.

## Why did I build it?
This specific project has a far fetched origin story, but the gist is that I wanted to do something with a 555 Timer after seeing a normal wristwatch, then comparing it with my smart watch, then thinking what is in the middle of the two - whether the thing I should make should be analog, or digital. 

After reasoning around with Gemini for a bit, I realised I would unfortunately have to use something closer to an oscillator rather than a 555 Timer as I hoped. In this chat, I also figured out how some of the other stuff would work, which brings us to our next section for those interested.

## How does it work? - _@techy people, this is for you_
The question we are all wondering. There is such a complex PCB and schematic we have seen in the photos, and now we at least know what it is - but how does it work? The simple answer can be broken into some few blocks and sections of the hardware, that eventually make the watch work. The blocks go as such:

1. Timer block (SG-3030CM gives a 32.768kHz pulse, then a 2^14 divider gets it down to 2Hz, then another divider to 1Hz) ---> 

2. Second to minute pulse block (two carry counter ICs that make the pulse 1/16Hz to input over to the display) ---> 

3. Display block (CD4026s that output to super small 0.2" segment displays) ---> 

4. And-gate wrap around (74HC08 IC that supplies quad 2 input and-gates for detecting certain segments)


## PCB and layout - _There is no greater optimism than ordering 500 boards without testing the prototype first._
As seen in the picture, the PCB is quite busy, with their being 701 trace segments, 258 pads, 73 vias, and a total of 123 nets. All these components have to fit in a wristwatch size of 35x42mm, and there are over 30 resistors and capacitors. To fit them all with enough space for a copper zone to pour, and to fit traces, I had to move over some parts to the back, but this means I will have to get a more advanced way of manufacturing it.

The way I was able to do this, with not much KiCAD experience was by logically splitting up the components, and wiring them one by one. this means I first made a display block with all the appropriate IC chips and resistors. After wiring them as needed, I then moved the m to a central position in the board to ensure there was enough space for the other components. then I fit in thew other timer units around where they could be inserted, before tracing them as well and then adding zones. I have two zones, on the back and front, for power and ground, and this meant I had to use many vias. To remove some random, useless copper zone islands, I had to use the 'do not fill' tool.

If you want a more chronological timeline of how I built this, check out my JOURNAL.md above!

## BOM - _NOT A BOMB!_
| Part | Where to buy | Cost |
| :--- | :---: | ---: |
| Segment Displays | [Ebay](https://www.ebay.co.uk/itm/195889276369?_skw=0.2%22+segment+display&itmmeta=01M6EP70M7ABXRD5BKFYGM1NHH&hash=item2d9be925d1%3Ag%3ATBIAAOSw2qplWLlX&itmprp=enc%3AAQALAAAA0CHNgUiiE%2FjQhlDTaMiAde8N4pqQcRs8IX6DydODM23mOmGth8nYc7n8xlrxr%2BS6NNEPMCjCPPxBPjypG0T%2B5PGzBhXTQX7kgbtBIbUk7yeaSZlJJ6amFuhsQ36oQ9b2yuffzb50OcMxg3q4ecM1aXkWZo%2F783288050KDa2ArMurpdlvRwuIxSIHRjXkyeuZAuIBqRyUxFpR0BJJzrU7XKouGydvSz2MxBBIo4o8Zub2EHKCbsUPWCddHyWID6wkAjNf4vrKmJSyS3vcDLDhIs%3D%7Ctkp%3ABk9SR7aKnNazaA&var=495722409176) | £6.00 |
| LiPo battery | [Amazon](https://www.amazon.co.uk/battery-200mAh-Lithium-Polymer-connection/dp/B0D7VSYPPV/ref=sr_1_1?crid=29NVIJLAAEKU9&dib=eyJ2IjoiMSJ9.X7pX1xi7ILp_yplrh-ou4Vn7LX2L5z4TSvIyitPoWCRTs833GjyNv_btAHxWWRVfidY4wBOOqi-bF9z36nFckCWh6gMjnExoc1Siyj5zNpM01Gdy7AxC1Yx6yceXOyPuezl3_dylYWErBcJeXORGgf_EmMsIkefHAp5C3YBVZepQy78KDg_m93ImNwE2-U-9F_XQ-JeKX3mFoFbwaYuhXktrl7TpZVMo1aGalGdQDR4.xiXYNVCcjwKY2whsgjaTlGsp_9Z_KdIO1XLzM3AwIMA&dib_tag=se&keywords=lipo%2Bbattery%2B3.7v%2Bsmall%2B200mAh&qid=1795460422&sprefix=lipo%2Bbattery%2B3.7v%2Bsmall%2B200mah%2Caps%2C161&sr=8-1&th=1) | £6.99 |
| Button | [AliExpress](https://www.aliexpress.com/item/1005012840797368.html?spm=a2g0o.productlist.main.5.443a124ch89hrB&algo_pvid=1b1f1828-bc73-4d8e-ac3d-791ba3cc20e5&algo_exp_id=1b1f1828-bc73-4d8e-ac3d-791ba3cc20e5-4&pdp_ext_f=%7B%22order%22%3A%225%22%2C%22eval%22%3A%221%22%2C%22fromPage%22%3A%22search%22%7D&pdp_npi=6%40dis%21GBP%212.21%212.07%21%21%212.81%212.63%21%400b0fe08917954597643931705e0eb7%2112000059495813788%21sea%21UK%216074049085%21X%211%210%21n_tag%3A-29919%3Bd%3A1f3ba004%3Bm03_new_user%3A-29895&curPageLogUid=LAaXCNjWhGwG&utparam-url=scene%3Asearch%7Cquery_from%3A%7Cx_object_id%3A1005012840797368%7C_p_origin_prod%3A) | ￡2.07 |
| JST port | [AliExpress](https://www.aliexpress.com/item/1005012356614470.html?spm=a2g0o.productlist.main.25.1ce37d798pSBfy&algo_pvid=5d2b104a-103d-42cd-820e-ac5102c88d9c&algo_exp_id=5d2b104a-103d-42cd-820e-ac5102c88d9c-24&pdp_ext_f=%7B%22order%22%3A%2265%22%2C%22eval%22%3A%221%22%2C%22fromPage%22%3A%22search%22%7D&pdp_npi=6%40dis%21GBP%211.31%211.21%21%21%2111.12%2110.23%21%400b5e1a3817954605730502025e0f96%2112000058175092939%21sea%21UK%216074049085%21X%211%210%21n_tag%3A-29919%3Bd%3A1f3ba004%3Bm03_new_user%3A-29895&curPageLogUid=Xan4gW2oVw1H&utparam-url=scene%3Asearch%7Cquery_from%3A%7Cx_object_id%3A1005012356614470%7C_p_origin_prod%3A) | ￡1.21 |

## Reviewer's note - _Bold of me to read the footnotes before understanding the title_
For the funding of this project, I have reached out to PCB way for there kind sponsorship programme, so the only parts that will need to be funded by Hackclub are the battery, button, case? (maybe), and finally the displays themselves.

Thank you to Hackclub Forge for helping bring this project to life!
