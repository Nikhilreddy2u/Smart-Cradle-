#include <dht.h>
#include<Servo.h>
#define moisturesensor A2
#define DHTTYPE DHT11
#define DHTPIN 2 
#define SoundSensorPin A1
Servo Myservo;
//Servo Myservo2;
int BUZZER=9;
dht DHT;
float sensorValue = 0;
int msvalue=0;
void setup()
{ 
        Serial.begin(9600);
        pinMode(moisturesensor,INPUT);
        pinMode(A2,INPUT);
        pinMode(SoundSensorPin,INPUT);
        Myservo.attach(3);
      //  Myservo2.attach(4);//digital pin of arduino
        pinMode(BUZZER,OUTPUT);
}
void loop()
{ 
  //Serial.println(sensorValue);
  readmoisture();

  readdht();
  readsound();
  if(sensorValue<=400)
            {  
              Serial.println("<:::::::::BABY IS CRYING:::::::::>");
              readservo();
            }
            else if(DHT.temperature > 33 && sensorValue<=400 && msvalue<=500)
            {
              Serial.println("BABY IS IN DANGER");
            }

  
}
void readmoisture()
{ 
  msvalue=analogRead(moisturesensor);
  Serial.println(msvalue);
  if(msvalue<500)
    {   
     Serial.println("<:::::::::::PEE DETECTED:::::::::>");
          for(int i=0;i<=21;i++ )
            {      
                digitalWrite(BUZZER,HIGH);
                delay(1000);
                digitalWrite(BUZZER,LOW);
                delay(1000);        
            }
    }
  
}
void readdht()
{ 
  
    // Reading temperature or humidity from DHT sensor
  int chk = DHT.read11(DHTPIN);
  Serial.print("Temperature = ");
  Serial.print(DHT.temperature);
  Serial.print(" Celsius\t");
  Serial.print("Humidity = ");
  Serial.print(DHT.humidity);
  Serial.println(" %");
  if(DHT.temperature > 33) {
        Serial.print(" <:::::::::::HIGH TEMPERATURE DETECTED:::::::::::>\t");
        digitalWrite(BUZZER, HIGH);
            delay(500);        
      } 
  else {
          digitalWrite(BUZZER, LOW);
            delay(500);        
      }
}
void readsound()
{ 
       for (int i = 0; i <= 4; i++) 
           { 
               sensorValue = sensorValue + analogRead(SoundSensorPin); 
               //delay(100); 
           } 
  sensorValue = sensorValue/10.0;
  Serial.println(sensorValue); 
  //delay(100); 
}
void readservo()
{
    
    for(int i=20;i<=50;i++){   
    Myservo.write(i);
    //Myservo2.write(i);  
    delay(30); 
    }
    for(int i=30;i>=40;i--){   
    Myservo.write(i);
    //Myservo2.write(i);  
    delay(30);
   
  
}
}
