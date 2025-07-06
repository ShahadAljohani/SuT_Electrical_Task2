# SuT_Electrical_Task2
Task 2 - Week 3 (Summer Training)

---------------
## About This Task
A task involving the simultaneous control of two servo motors moving in opposite directions.

* Components used:

                Arduino
                BreadBoard
                2 servo motors
                jumper wires
---------------
### Servo motor simple explanation:
   ![Screenshot (522)](https://github.com/user-attachments/assets/81215860-40b0-4aa3-a6d0-e8434710188f)

   As shown in the picture above it does contain several commponents including DC motor.
   - DC motor: core component providing the rotational force.
     
   - Gearbox: system of gears increasing the motor's torque and decrease the speed of the motor, with increasing its strength.

   - Servo Horn: arm which it gives place to attach whatever you want to move.
     
   - Potentiometer: resistor acts as a position sensor, it tells the controller where the motor is positioned. **HOW?** since it's connected directly to the output shaft(the                         part that is actually rotates), the potentiometer's resistance changes.
     
   - Control unit: receives signals from external controller (arduino), it checks the potentiometer's position then controls the DC motor.

------


   * How does it work?
       Servo motor receives a PWM signal that tells it what angle to move to, the controller reads the signal, then it compares the current position with the target, the
       motor rotates through gears to reach the angle.

   * What's the difference between servo motor and DC motor?
        Servo motor moves based on a positioned angle which is limited by a specific angle (self-adjustes position).
       
        While the DC motor rotates freely and has a continous rotation.
       
        servo = positioning, DC = Spinning
   
  * Why does it contains several sizes (small, medium, industrial-size)?

      Because of the different application needs =  diffferent amount of power, precision, physical space and torque requirements.

 * Based on what there becomes an industrial-size?

      It's based on engineering factors and environmental demands. Industrial applications require high torque, higher voltage, and precise control.

   ---------------
   ## Hardware Configuration:

   ### using a simulator:
  
   ![Screenshot (523)](https://github.com/user-attachments/assets/bd1838b7-8295-4dc8-9827-530cb81dbb60)


in this simulation i didn't use a breadboard to make it simpler and more clear.

   ### using Arduino
   
  ![SuT_Electrical2](https://github.com/user-attachments/assets/de53e7c6-c5b6-4101-8094-d461f8f76280)
   ---------------
  ## Implementation: 

```
#include <Servo.h>

Servo myservo;  // create servo object to control a servo
Servo myservo2;
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position
int pos2 = 180;

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
  myservo2.attach(10);
}

void loop() {
  // Move servo1 0 → 180, servo2 180 → 0
  for (pos = 0, pos2 = 180; pos <= 180 && pos2 >= 0; pos++, pos2--) {
    myservo.write(pos);
    myservo2.write(pos2);
    delay(15);
  }

  // Move servo1 180 → 0, servo2 0 → 180
  for (pos = 180, pos2 = 0; pos >= 0 && pos2 <= 180; pos--, pos2++) {
    myservo.write(pos);
    myservo2.write(pos2);
    delay(15);
  }
}

```
