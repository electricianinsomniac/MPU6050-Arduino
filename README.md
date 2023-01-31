# MPU6050-Arduino
Arduino run mpu6050 sensor gyroscope

# Introduction
This project aims to develop a robot that can be controlled using the movements of a user's hand. The robot will have an MPU6050 sensor attached to it, which will be used to measure the orientation of the user's hand. Based on the orientation, the robot will move in a particular direction.

# Objective:
The objective of this project is to use the MPU6050 sensor to measure the orientation of the user's hand and use that information to control the movement of a robot.

# Methodology:
- Assemble the robot and attach the MPU6050 sensor to it
- Connect the MPU6050 sensor to the Arduino board
- Write and upload code to the Arduino board to get the orientation data from the MPU6050 sensor
- Use the orientation data to control the movement of the robot

# Expected Outcome
The expected outcome of this project is a working motion-controlled robot that can be controlled using the movements of a user's hand.

# Applications
This project can be used for educational purposes, as it demonstrates the use of the MPU6050 sensor and the Arduino platform for controlling the movement of a robot. It can also be used for entertainment purposes, as it allows for a new and interactive way of controlling a robot.

# Knowledgement
You can download the MPU6050 library for the Arduino platform from the following link:

https://github.com/jrowberg/i2cdevlib/tree/master/Arduino/MPU6050

To install the library in your Arduino IDE, go to Sketch -> Include Library -> Add .ZIP Library, then select the downloaded .zip file.

# Example Code
Here is an example code to get the pitch, roll, and yaw data from the MPU6050 sensor using the Arduino platform:
```
#include <Wire.h> 
#include <I2Cdev.h> 
#include <MPU6050.h> 

MPU6050 accelgyro; 

void setup() { 
  Serial.begin(9600); 
  accelgyro.initialize(); 
} 

void loop() { 
  int16_t ax, ay, az; 
  int16_t gx, gy, gz; 
  accelgyro.getMotion6(&ax, &ay, &az, &gx, &gy, &gz); 
  
  float pitch = atan2(ax, sqrt(ay*ay + az*az)) * 180/PI; 
  float roll = atan2(ay, sqrt(ax*ax + az*az)) * 180/PI; 
  float yaw = atan2(sqrt(ax*ax + ay*ay), az) * 180/PI; 

  Serial.print("Pitch: "); 
  Serial.println(pitch); 
  Serial.print("Roll: "); 
  Serial.println(roll); 
  Serial.print("Yaw: "); 
  Serial.println(yaw); 
  delay(500); 
}
```
Note: You'll need to install the MPU6050 library for the above code to work.
