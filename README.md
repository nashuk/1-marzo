# 1-marzo
Entradas analógicas + Salidas PWM = 3 Potenciometros + LED RGB

int ledRojo = 9;
int ledVerde=10;
int ledAzul=11;

int pinPot0 = A0;  
int pinPot1 = A1; 
int pinPot2 = A2; 

int valorsensor0=0;
int valorsensor1=0;
int valorsensor2=0;

float divisionR; 
float divisionV;
float divisionA;
              
void setup() {
  pinMode(ledRojo,OUTPUT);  
  pinMode(ledVerde,OUTPUT);
  pinMode(ledAzul,OUTPUT);
  Serial.begin(9600);

}

void loop() {
    float Constante = (float) 225 / 1023;

   valorsensor0 = analogRead(pinPot0);
   valorsensor1 = analogRead(pinPot1);
   valorsensor2 = analogRead(pinPot2);

   divisionR = Constante * valorsensor0;    
   divisionV = Constante * valorsensor1;
   divisionA = Constante * valorsensor2;

   color(divisionR,divisionV,divisionA);

}
void color(int rojo, int verde, int azul){
    analogWrite(ledRojo, 255-rojo);
    analogWrite(ledVerde, 255-verde);
    analogWrite(ledAzul, 255-azul);

  }
