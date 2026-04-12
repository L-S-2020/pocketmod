# Welcome to pcb design

Note: This guide is intended for participants, with none to little experience in pcb/ hardware design. If you just want to get started, check out our quick start guide.

Hi, so you want to make your own pc gadget for pocketmod, nicee. 
Today we're going to design a little light for your keyboard, while I'll show you the basics of pcb design.

![image](https://cdn.hackclub.com/019d77c9-a8f9-7011-a5a0-f9d1d2f8488e/paste-1775831196488.png)

## Set up

In this tutorial we'll be using Kicad, an open source pcb design tool which is free to use and really great.
So first of all download kicad from their [website](https://www.kicad.org/download/) and install it.
After the installation, you should see this homescreen:

![image](https://cdn.hackclub.com/019d747b-b935-7899-857e-13f628dee176/paste-1775775757728.png)

From here we will start by creating a new project by clicking on **File -> New Project** selecting the default template and the location to store the project.

With this done, you see that kicad has already created two files within our project, a .kicad_sch , for the schematic and a .kicad_pcb for the pcb design. 

![image](https://cdn.hackclub.com/019d7486-26a8-7897-affc-6219a9a1e894/paste-1775776440622.png)


## Drawing the schematic

The schematic is what defines all the connections of your pcb, so let's start with it.
First open the schematic editor by clicking on the schematics button.

![image](https://cdn.hackclub.com/019d7499-59e4-77b5-ae88-4366c0551fb0/paste-1775777699614.png)

At first the UI may seems a bit overwhelming, but it's structured very logically.

![image](https://cdn.hackclub.com/019d74a0-2dee-7cc8-81f7-672834ad60dc/paste-1775778146754.png)

On the right side you can find the tools for editing your schematic. Press a to open the symbol insert window (a symbol is the representation of a component in your schematic). Here you find a list of components, search for USB and select a vertical usb a plug.

![image](https://cdn.hackclub.com/019d74ad-fdfd-774b-b044-3dd6e6a031c3/paste-1775779051941.png)

You can see that the symbol you just placed exposes the connectors, the component has, as little red lines.

![image](https://cdn.hackclub.com/019d74b1-9d1c-7e59-bf83-1ae5508774b5/paste-1775779289665.png)

Additionally to the connector, our light also needs something to shine, so let's add a few leds.

![image](https://cdn.hackclub.com/019d74d9-e0c7-7693-a33f-1db3b8ee1964/paste-1775781927907.png)

As our leds only need about 3v and the USB will give us 5v of power we need some way to get this power down. One simple to do this is by just placing some strong resistors in front of our leds. To calculate this, we can use this simple formular:  
R = (Vusb - Vled) / Iled  
For our test leds with 3v and 25mA (=0.025 A) this comes down to R = (5-2) / 0,025 = 120 Ω. 
So let's add the resistors, one for each LED.

![image](https://cdn.hackclub.com/019d74f7-d4f4-79b8-9439-4b93d8c3f408/paste-1775783891175.png)

Connect them to front of the LEDs, then open the symbol properties by double clicking on the resistor symbol.
Under value enter the 120 Ω we calculated before and press enter. Repeat this for every resistor.

![image](https://cdn.hackclub.com/019d7768-d823-76d5-a802-00cb69edba4b/paste-1775824851388.png)

Now your schematic should look something like this, if you want to rotate a symbol you can do that by selecting it and pressing r.

![image](https://cdn.hackclub.com/019d7777-f3f6-74fb-bbff-0e1f388c1439/paste-1775825842030.png)

As we've placed all the symbols we need, we can now wire them up. In the right sightbar select the wire tool (5th icon from the top) and place wires like this.

![image](https://cdn.hackclub.com/019d777b-4d70-7840-8664-012fa52873e8/paste-1775826061998.png)

Congrats, you've just created your first schematic🎉.
So lets turn it into a pcb.

## Designing the pcb

Now we have to tell Kicad how the symbols in our schematic look on the pcb. That's done using so called footprints, they tell kicad how to connector pads or holes for the component look like.  
Lets start by opening the footprint assignment tool, with this button in the top bar.

![image](https://cdn.hackclub.com/019d7787-3dc8-75b9-9106-ed484d12e09d/paste-1775826844518.png)

In the footprint assignment tool, assign the footprints by selecting a symbol in your schematic from the middle and then double clicking on the according footprint on the right.
Assign the footprints like this and then press ok.

![image](https://cdn.hackclub.com/019d778b-c54d-7c33-b038-43931adbcec4/paste-1775827140417.png)

As kicad now knows how the components on our pcb will look, we can switch to the pcb design tool, by clicking on this button:

![image](https://cdn.hackclub.com/019d778d-8b1a-7dd2-8113-f22e9a0dfd42/paste-1775827257545.png)

In the design tool, use the "Update PCB from schematic" button to automatically import the components from the schematic on your pcb.

![image](https://cdn.hackclub.com/019d7790-f896-7aa9-8618-1d574bf4aab0/paste-1775827481703.png)

Place the components on the pcb by clicking and arrange them like this (drag and drop). The way you arrange your components here will determine how they will be placed on the pcb. Make sure to leave enough space between the usb plug on the LEDs to fit on the side of your pcb or laptop.

![image](https://cdn.hackclub.com/019d7796-6c70-7bb5-b7fa-afb5adaf6280/paste-1775827839439.png)

Then we can go on placing the wires on the pcb. Select the routing tool from the right side bar.

![image](https://cdn.hackclub.com/019d779b-2f08-71af-842b-45e46c0b6494/paste-1775828151295.png)  

The lines you can see in light blue show you which components should be connected together, go ahead and wire this connections together.
It should look something like this:

![image](https://cdn.hackclub.com/019d779f-47c9-7c71-aa2f-cb8e663ca49e/paste-1775828419370.png)

Now we just have to tell Kicad what size our the pcb should have in the end. You can do that by selecting the edge.cuts layer in the right sidebar and then drawing a rectangle around your components.
![image](https://cdn.hackclub.com/019d77a3-0d9b-7fd9-8a5f-bb9a64e9c8d3/paste-1775828666763.png)
![image](https://cdn.hackclub.com/019d77a4-cff7-75a7-af80-1e0903651173/paste-1775828782095.png)

You can click the 3d viewer icon to see your pcb in 3d.
![image](https://cdn.hackclub.com/019d77a5-8d82-7cec-aa17-abf5d82efc05/paste-1775828830690.png)

Congrats, you've just designed your first pcb🎉.

![image](https://cdn.hackclub.com/019d77a6-d3ca-7469-9169-1badc8ea23fe/paste-1775828914399.png)

## Next steps

You've just made a simple USB powered keyboard light, but of course there's a ton of other cool stuff out there.  
For your pocketmod I would recommend you should start by defining a basic feature it should have, build it and then add more features, rather than starting with a huge mountain of requirements and no idea where to start.  
If you still need some inspiration, use the idea generator on the pocketmod website or look at submissions in the gallery. You can also have a look at their schematics to understand what the creators exactly did.

For some additional tips and tricks, look in the additional resources tab.