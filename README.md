# Hawkeye2_frame_by_frame
The purpose of this project is to prvide the instruction to the user on how to modify the existing 8mm film projector for the frame-byframe capture directly into the camera using a small MSP430 based board.  
Generally the projects of this type require several modifications to the projector including the light change, motor change and addition of some type of a trigger detector for the camera.  
This project also requires the light change and the motor change, but unlike similar other projects, it does not require the trigger mechanism. The trigger is pprovided by the MSP430 controller. The controller is programmed to precisely control the stepper motor rotation so that the film gets advanced exactly one frame at the time. The camera trigger is then generated at the end of frame advance.  

System Components

![IMG_20220504_144707](https://user-images.githubusercontent.com/48537944/166855115-0297680d-0524-4b80-a290-e62c47861d60.jpg)

At the heart of the system is the Hawkeye2 controller. This is an open source design board. 
