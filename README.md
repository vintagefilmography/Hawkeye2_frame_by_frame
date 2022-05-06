# Hawkeye2_frame_by_frame
The purpose of this project is to prvide the instruction to the user on how to modify the existing 8mm film projector for the frame-byframe capture directly into the camera using a small MSP430 based board.  
Generally the projects of this type require several modifications to the projector including the light change, motor change and addition of some type of a trigger detector for the camera.  
This project also requires the light change and the motor change, but unlike similar other projects, it does not require the trigger mechanism. The trigger is pprovided by the MSP430 controller. The controller is programmed to precisely control the stepper motor rotation so that the film gets advanced exactly one frame at the time. The camera trigger is then generated at the end of frame advance.  

System Components

![IMG_20220504_144707](https://user-images.githubusercontent.com/48537944/166855115-0297680d-0524-4b80-a290-e62c47861d60.jpg)

## Hawkeye2 Controller  
At the heart of the system is the Hawkeye2 controller. This is a custom design. All design info is available gere is this repository. The board details are included in  the homemade-v3 folder. Download the folder to your Eagle project directory and there you will have access to the schematic and the board layout. 
The MSP430 micro controller firmware is available in the MSP folder. Download the zip file from there and save it in you TI Code Composer project directory. From there you can edit the source and flash the target by using TI Launchpad.  
There are two more boards included. One is for the front panel switches and the other is for the switch interface board. Follow the included wiring diagram to interconnect the system.
## Stepper Driver  
The stepper driver is an off the shelf product. 
https://www.amazon.com/gp/product/B075HBJP51/
There are many other variants available. This particular one is a good choice because it has 256 micro steps allowing for a very precise tuning control. One disadvantage is that it operates from a 24VDC source so that 2 DC adaprers are required, one for the driver and the other one for the controller that requires 12VDC source.  
Driver dip switches  
The following is recommended:
SW4 - Half Currect
Current - 
1.4A for this type motor https://www.amazon.com/gp/product/B00PNEQKC0/
2.7A for this type motor https://www.amazon.com/gp/product/B00PNEPF5I/
Set the pulse/rev switches for the highest speed that can still hold the torque and there is no skipping of steps. Skipping will result in loss of synchronization.  
## Stepper Motor  
These two motors were tested.
1.4A for this type motor https://www.amazon.com/gp/product/B00PNEQKCdesigned with Spark0/
2.7A for this type motor https://www.amazon.com/gp/product/B00PNEPF5I/
You will have to design a bracket for the motor so that it fits properly in the projector after you remove the old motor. 
A sample stepper bracket is included here as a good staring point. Use the Designspark Mechanical free software to modify the bracket for your projector.

## Pulley
There are quite a few pulleys avaliable online.  
Example:  
https://www.amazon.com/gp/product/B07C4R3PGV/  
https://www.amazon.com/gp/product/B07C4QD1BV/
You can also design your own. A sample design will be included here shortly.

## Belt
This used to be a big problem but with the neophrene Urethane belting that became available it is easy to make your own custom belt.
https://www.amazon.com/gp/product/B07L3W7Z1N  
Follow the following instructions:  
https://www.youtube.com/watch?v=mBtHvPWVgDw

## Control Switches:


![front_panel](https://user-images.githubusercontent.com/48537944/167196521-d25ae0d0-ba29-4e8c-b0fa-85e9202a8518.png)

The control switches control the operation of the unit.  
### RUN Switch
Pauses the operation  
### ALIGN
Slowly advances the film until the frame is centered in the camera. Also turns tuning on if activated in run mode.  
### REW
Turns takeup continuously on if run switch is off.  
The switch can also be used in conjuction with the PROJ switch to select the projector type. 
I.e. if the setup is used with multiple projectors then the projector synchronization can be saved in non volatile memory.  
Four memory locations are available:   
REW     PROJ  
0       0       Projector1  
0       1       Projector2  
1       0       Projector3  
1       1       Projector4  
The switches are active only during a short time after the power is plugged in and in most cases the only Projector1 selection will be used.  


### PROJ 
Seects the projector type used. In most cases this switch will be kept off. 
The projector selection is read by the firmware upon board power up and cannot be changed after that during normal operation.  
### UP and DOWN switches 
Used during tuning mode to run change the length of stepper advance.  
### Up and DOWN buttons
Located on the controller board, used for fine tuning of the stepper  
### REV Switch 
Reverses the motor rotation for film rewind.  

## Operation
Very straight forward. Here is a short video showing the operation.  
https://photos.app.goo.gl/MLEgviiinpVREHCQA  
As the video shows, plug the power in for both the controller and the driver and then flip the ADV switch on until the projector is finished with the film frame advance and at that point turn the ADV switch off. Then, connect the camera trigger and turn the camera on. Turn the RUn switch on the the camera will start capturing the farmes. If at any point the system starts goung out of sync you can resync it by using the ADV switch or alternatively, turn the ALG switch on and the hit the UP or DOWN button just once.   
The UP button makes the run shorter and the DOWN button makes it longer.  

## Tuning the Stepper  
Turn the RUN switch on. Make sure all other switches are off.
![image](https://user-images.githubusercontent.com/48537944/167198893-b7b94d33-e3a4-4934-8207-8972e0525aaf.png)

Turn the ALIGN switch on.  
This puts the controller into tuning mode.  
Turn on the DOWN switch. This makes the stepper step one count longer.  
While the DOWN switch is still on, turn on the UP switch.  
This will cause continuous stepper count increase. You will see that the film advance becomes larger and larger.   
After a while the stepper motor advance will  be close to one full turn of the projector cam.  
Once the alignment is close to a full cam rotation, turn the UP switch off and then the DOWN switch off.   
Continue with fine tuning by using the controller board mounted UP and DOWN buttons.  
The UP button will make the advance shorter by one count and conversely, the DOWN button will make it longer by one count.  
Once the alignment is done DO NOT POWER THE BOARD DOWN.  
Turn the ALIGN switch off and then the RUN switch off. Then you can power the board down.  
Power the board up again with the correct memory selected.
Turn the RUN switch on and check that the alignment was restored properly from the memory.  
It is to be noted that the UP and DOWN sequence can be reversed if the Film advance is too large.  
In that case turn the UP switch on first followed by the DOWN switch.   
Once done, turn the DOWN switch off first followed by the UP switch.







