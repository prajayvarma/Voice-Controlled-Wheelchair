# Voice-Controlled-Wheelchair

Voice-Controlled Wheelchair 🚀

👨‍💻 Author

prajay varma (230003018)
B.Tech Mechanical Engineering
IIT Indore

📌 Abstract

This project presents the design and development of a low-cost, Bluetooth-based voice-controlled wheelchair that enables physically challenged individuals to navigate using simple verbal commands. The system converts voice commands into motion instructions using Arduino and a motor driver shield.

The primary goal is to create an affordable, accessible, and easy-to-use assistive mobility solution using open-source embedded systems.

🎯 Objectives

Enable hands-free wheelchair control using Bluetooth-transmitted voice commands.

Ensure smooth, safe, and reliable motor operation.

Develop a cost-effective prototype using Arduino components

Create a scalable platform for future smart enhancements.

🧩 Hardware Components

Component	Description
Arduino UNO	              ----->     Main controller that processes Bluetooth commands

HC-05 Bluetooth Module	  ----->        Receives wireless commands from smartphone

L293D Motor Driver        ----->           Shield	Controls DC motor direction and speed

2 DC Motors	              ----->           Provide forward,backward and turning motion

External Battery	        ----->           Supplies power to motors and Arduino

Power Switch	            ----->            Turns system ON/OFF

🔌 Circuit Connections

HC-05 TX → Arduino Pin 10

HC-05 RX → Arduino Pin 11

Motor Shield mounted directly on Arduino UNO

Motor 1 connected to M1

Motor 2 connected to M2

External battery connected to motor shield

⚙️ System Working

User gives voice command via smartphone.

Smartphone converts speech into characters:

F (Forward)

B (Backward)

L (Left)

R (Right)

S (Stop)

Command transmitted via Bluetooth.

Arduino receives command.

Motor driver activates motors accordingly.

Wheelchair moves in desired direction.

🕹️ Command Mapping

Character	Action
F	Move Forward

B	Move Backward

L	Turn Left

R	Turn Right

S	Stop

💻 Arduino Program

#include <AFMotor.h>

AF_DCMotor motor1(1);
AF_DCMotor motor2(2);

char command;

void setup() {
  Serial.begin(9600);
  motor1.setSpeed(200);
  motor2.setSpeed(200);
}

void loop() {

  if (Serial.available() > 0) {
    command = Serial.read();

    switch(command) {

      case 'F':
        motor1.run(FORWARD);
        motor2.run(FORWARD);
        break;

      case 'B':
        motor1.run(BACKWARD);
        motor2.run(BACKWARD);
        break;

      case 'L':
        motor1.run(FORWARD);
        motor2.run(BACKWARD);
        break;

      case 'R':
        motor1.run(BACKWARD);
        motor2.run(FORWARD);
        break;

      case 'S':
        motor1.run(RELEASE);
        motor2.run(RELEASE);
        break;
    }
  }
}

✅ Advantages

Hands-free mobility control
Low-cost implementation
Open-source platform
Easy to customize and expand
Compact and simple two-motor mechanism

⚠️ Limitations

Voice recognition errors in noisy environments
Requires periodic battery charging
Basic Bluetooth range limitation

🚀 Future Enhancements

Ultrasonic sensor-based obstacle avoidance
AI-based voice recognition
GPS tracking integration
IoT-based remote monitoring
Emergency automatic braking system

📊 Applications

Assistive mobility devices
Hospitals and rehabilitation centers
Elderly care support systems
Smart mobility research projects

📌 Conclusion

The Bluetooth-based voice-controlled wheelchair demonstrates how affordable embedded systems can improve independent mobility. By combining Arduino, Bluetooth communication, and motor control, a simple yet effective assistive technology solution is achieved
