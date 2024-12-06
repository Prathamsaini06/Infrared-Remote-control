# Infrared-Remote-control
#include <IRremote.hpp>

const int rcvPin=3;

IRrecv irrecv(rcvPin);

decode_results results;

void setup()
{ 
  Serial.begin(9600);
   irrecv.enableIRIn(); // Start the receiver
    
  pinMode(5, OUTPUT);

  
}
void loop() {
  
  if(IrReceiver.decode()) {
    auto value= IrReceiver.decodedIRData.decodedRawData; 	
    //switch(results.value)
      switch(value)
      {        
        case 4010852096:
            Serial.println("1");  // Button 1
        	digitalWrite(5,HIGH);
          	break;
          
        case 3994140416: // Template
              Serial.println("2");  // Button 
        	  digitalWrite(5,LOW);
         	  break;
                
 
        default: Serial.println(value);     
      }  
    IrReceiver.resume(); // Receive the next value
  }
  
}
