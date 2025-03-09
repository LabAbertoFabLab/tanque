# Tanque
O código apresentado aqui pretende ser usado para controlar um tanque através de telemóvel com recurso ao bluetooth (BT)

## Introdução ao BT
Nesta parte iremos controlar o LED com o telemóvel através de BT.
```
/*
 Controlar o LED com o BT
*/

// declaração de variáveis
//variável caracter/número para leitura da comunicação UART 
char comando;
#define LED 13

// a função setup corre uma vez apenas no inicio ou sempre que se carrega no botão reset
void setup() {
  // initialize digital pin LED as an output.
  Serial.begin (9600);
  pinMode(LED, OUTPUT);
}

// a função loop está sempre a funcionar
void loop(){
  comando = Serial.read();
  if (comando =='1'){digitalWrite(LED,HIGH);} 
  else if (comando =='2'){digitalWrite(LED,LOW);}
  delay(50);                  	// espera 0,05 s
}
```

## Controlar apenas o movimento 

```
//Controlar um tanque de lagartas em dois movimentos apenas, para a frente e marcha atrás
int V1 = 3;  
int M1 = 12;
int V2 = 11;                        
int M2 = 13; 

char comando;

void setup()
{
    pinMode(M1, OUTPUT);  
    pinMode(M2, OUTPUT);
    Serial.begin(9600);
}

void loop(){

Serial.write (comando = '0');// escreve na comunicação serial o comando de parar

if (Serial.available() > 0) {
comando = Serial.read();
}

if( comando == '1' ) {
    digitalWrite(M1,HIGH);  //direção frente
    digitalWrite(M2, HIGH); //direção frente     
    analogWrite(V1, 150);   // PWM velocidade, usar valor entre 0 e 255
    analogWrite(V2, 150);   // PWM velocidade, usar valor entre 0 e 255
    delay(1000); //avança 1s
    }
if( comando == '2' ) {    
    digitalWrite(M1,LOW);  
    digitalWrite(M2, LOW);      
    analogWrite(V1, 150);   
    analogWrite(V2, 150);   
    delay(1000);

} else if( comando == '0' ) {     
    analogWrite(V1, 0);   // pára
    analogWrite(V2, 0);   // pára
    delay(50);
    }
//Serial.println(comando); //testar
}

```

> References:
> Oficina: https://docs.google.com/document/d/e/2PACX-1vReJHYMIyNauPT-5F4sWZQ51mNibV4wYyDqK_BIMdSpeU8AEdPi917PMntFjTr1pRi9wXBQw4fn4wRT/pub
> https://wiki.keyestudio.com/Ks0007_keyestudio_L298P_Motor_Shield
> https://projecthub.arduino.cc/drone_proton/bluetooth-controlled-rc-tank-d22a82
> ROBOBOY APP: https://www.youtube.com/watch?v=QeTW3S2LFO0 
