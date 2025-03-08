# tanque
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
  else if(comando =='2'){digitalWrite(LED,LOW);};
  } else {digitalWrite(LED,LOW);};
   delay(50);                  	// espera 0,05 s
}
```

## Controlar apenas em frente e marcha atrás
Código inicial

```
int E1 = 3;  
int M1 = 12;
int E2 =11;                        
int M2 = 13;                          

void setup()
{
    pinMode(M1, OUTPUT);  
    pinMode(M2, OUTPUT);
    Serial.begin(9600);
}

void loop()
{
 if (Serial.available() > 0) {
char BT = Serial.read();
Serial.println(BT);

if( BT == '1' ) {
    digitalWrite(M1,HIGH);  //direção frente
    digitalWrite(M2, HIGH); //direção frente     
    analogWrite(E1, 100);   // PWM velocidade
    analogWrite(E2, 100);   // PWM velocidade
    delay(50);
    }
if( BT == '2' ) {    
    digitalWrite(M1,LOW);  
    digitalWrite(M2, LOW);      
    analogWrite(E1, 100);   
    analogWrite(E2, 100);   
    delay(50);
}
```

> References:
> https://wiki.keyestudio.com/Ks0007_keyestudio_L298P_Motor_Shield
