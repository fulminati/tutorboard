# tutorboard

- 64 LDR
- 64 Diodi 1N4148
- 8 da 10k resistenze 




```c
const int ldr[8] = {A0, A1, A2, A3,A4,A5,A6,A7};  
 const int vccPin[8] = {2,3,4,5,6,8,9,10};  
 int ldrValue;  
 void setup() {  
  Serial.begin(9600);  
  pinMode(vccPin[0], OUTPUT);   
  pinMode(vccPin[1], OUTPUT);   
  pinMode(vccPin[2], OUTPUT);   
    pinMode(vccPin[3], OUTPUT);   
  pinMode(vccPin[4], OUTPUT);   
  pinMode(vccPin[5], OUTPUT);  
    pinMode(vccPin[6], OUTPUT);   
  pinMode(vccPin[7], OUTPUT);   
  
 }  
 void loop() {  
   for(int i = 0; i < 8; i++)  
   { 

    digitalWrite( vccPin[i],HIGH);  
      for(int j = 0; j < 8; j++)  
      {  
       ldrValue = analogRead(ldr[j]); 
       ldrValue = constrain(ldrValue, 0, 800); // ajusta valor lido  
       ldrValue = map(ldrValue,0,800,0,255); // le o LDR correspondente  
      // ldrValue = constrain(ldrValue, 0, 800); // ajusta valor lido  
     //  ldrValue = map(ldrValue,0,800,0,255);  // ajusta valor lido  
       Serial.print(ldrValue);
       Serial.print("  ");
       delay(500);// envia valor via porta serial   
       
      }  
    digitalWrite( vccPin[i],LOW);  
       Serial.println(); 
   }
    Serial.println("Nuova lettura"); 
          
 } // fim do loop principal  
 void estabeleceContato() {  
   while (Serial.available() <= 0) {  
   Serial.write('A');  // envia A ate estabelecer contato  
   delay(300);  
  }  
  }

```




## Related
- http://tecnomelque.blogspot.com/2012/08/arduino-ldr-matriz.html

