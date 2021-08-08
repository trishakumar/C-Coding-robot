#include<SR04.h>      // include the ultrasonic libraries 
const int ting = A0;   // define the pin ting of ultrasonic sensor as A0
const int echo = 2;   // define the pin echo of ultrasonic sensor as D2
SR04 sr04 = SR04(echo,ting);   // build the ultrasonic sr04
long a,a1,a2;     // define the variable a, used to save the measured distance from ultrasonic sensor.

const int PWMA = 5;  // define the speed of left motor as pin D5
const int PWMB = 6;  // define the speed of right motor as pin D6
const int INT_A = 4;  // define the speed of left motor as pin D4
const int INT_B = 7;  // define the speed of right motor as pin D7

const int S = 13;  // define the buzzer pin as D13

void setup() 
{
   Serial.begin(9600);   // set the serial port baud rate to 9600
   pinMode(PWMA,OUTPUT);  // set the control pin of motor as OUTPUT
   pinMode(PWMB,OUTPUT); 
   pinMode(INT_A,OUTPUT);
   pinMode(INT_B,OUTPUT);
   pinMode(S,OUTPUT);  // set the control pin of buzzer to OUTPUT
}

void loop() 
{
   a=sr04.Distance();    // detect the distance and assign to a
   Serial.print(a);     // print the a value on serial monitor
   Serial.println("cm"); // print the character cm and line wrap
   delay(10);   //delay 100ms
   if(a<20)     // if the measured distance is less than 20cm
   {
    Stop();   // stop
    delay(1000);
    back();
    delay(1000);    
    left();
    delay(430);
    Stop();                                                                                                           
    a1 = sr04.Distance();    //detect the distance and assign to a1
    delay(1000);
    left();
    delay(430);
    front();
   }
   else   // The measured distance is greater than or equal to 25
   {
    front();  // go forward
   }
}


// go forward
void front()    
{
  digitalWrite(INT_A,HIGH);  //left motor turns forward
  digitalWrite(INT_B,HIGH);   // right motor turns forward
  analogWrite(PWMA,100);   // speed of left motor（PWM=100)
  analogWrite(PWMB,100);   // speed of right motor（PWM=100)
}
// backward 
void back()   
{
  digitalWrite(INT_A,LOW);   // left motor turns backward
  digitalWrite(INT_B,LOW);  // right motor turns backward
  analogWrite(PWMA,100);   //speed of left motor（PWM=100)
  analogWrite(PWMB,100);   // speed of right motor（PWM=100)
}
// turn left
void left()   
{
  digitalWrite(INT_A,LOW);  // left motor turns backward
  digitalWrite(INT_B,HIGH);  // right motor turns forward 
  analogWrite(PWMA,80);   // speed of left motor（PWM=80)
  analogWrite(PWMB,80);   // speed of right motor（PWM=80)
}
// turn right
void right()   
{
  digitalWrite(INT_A,HIGH);   // left motor turns forward 
  digitalWrite(INT_B,LOW);   // right motor turns backward
  analogWrite(PWMA,80);   // speed of left motor（PWM=80)
  analogWrite(PWMB,80);   // speed of right motor（PWM=80)
}
// stop
void Stop()    
{
  digitalWrite(INT_A,LOW);
  digitalWrite(INT_B,LOW);
  analogWrite(PWMA,0);  // speed of left motor（PWM=0)
  analogWrite(PWMB,0);  // speed of right motor（PWM=0)
}
