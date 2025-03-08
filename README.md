# tanque
Tanque controlado por BT

Código inicial
'int E1 = 3;  
int M1 = 12;
int E2 =11;                        
int M2 = 13;                          

void setup()
{
    pinMode(M1, OUTPUT);  
    pinMode(M2, OUTPUT);
}

void loop()
{
    digitalWrite(M1,HIGH);  
    digitalWrite(M2, HIGH);      
    analogWrite(E1, 200);   // PWM regulate speed
    analogWrite(E2, 200);   // PWM regulate speed
    delay(8000);
    digitalWrite(M1,LOW);  
    digitalWrite(M2, LOW);      
    analogWrite(E1, 200);   //PWM regulate speed
    analogWrite(E2, 200);   //PWM regulate speed
    delay(8000);
}
'

References:
https://wiki.keyestudio.com/Ks0007_keyestudio_L298P_Motor_Shield
