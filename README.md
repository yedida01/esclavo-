# esclavo-//codigo esclavo
#include <SoftwareSerial.h>
SoftwareSerial mensaje(2,3);
#define echoPin 8 // Pin Echo
#define trigPin 9 // Pin Trigger
float duration; // duracion y distancia (tipo flotante)
double distancia = 0;
double sensor=0;
String info;
void setup() {
  Serial.begin(9600); 
  delay(200);
  mensaje.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);  
}

void loop() {
  
   sesor();

}

void sesor(){
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);

  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);

  sensor = float (duration * 0.017);

  distancia = 24.6-(sensor);
  //info=distancia;
  Serial.println(distancia);
  mensaje.write(distancia);
  delay(100);
  }
