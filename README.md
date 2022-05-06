# Hawkeye2_frame_by_frame
The purpose of this project is to prvide the instruction to the user on how to modify the existing 8mm film projector for the frame-byframe capture directly into the camera using a small MSP430 based board.  
Generally the projects of this type require several modifications to the projector including the light change, motor change and addition of some type of a trigger detector for the camera.  
This project also requires the light change and the motor change, but unlike similar other projects, it does not require the trigger mechanism. The trigger is pprovided by the MSP430 controller. The controller is programmed to precisely control the stepper motor rotation so that the film gets advanced exactly one frame at the time. The camera trigger is then generated at the end of frame advance.  

System Components

![IMG_20220504_144707](https://user-images.githubusercontent.com/48537944/166855115-0297680d-0524-4b80-a290-e62c47861d60.jpg)

Hawkeye2 Controller
At the heart of the system is the Hawkeye2 controller. This is a custom design. All design info is available gere is this repository. The board details are included in  the homemade-v3 folder. Download the folder to your Eagle project directory and there you will have access to teh schematic and the board layout. 
The MSP430 micro controller firmware is available in the MSP folder. Download the zip file from there and save it in you TI Code Composer project directory. From there you can edit teh source and flash the target by using TI Launchpad.  
There are two more boards included. One is for teh front panel switches and the other is for the switch interface board. Follow the included wiring diagram to interconnect teh system.
