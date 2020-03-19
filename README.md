# minor-project
*LDR--LIGHT DEPENDENT RESISTOR(its a light contollable resistor)(its resistance increases with increase in light intensity)
  
  Principle:
principle of this color detector is light of a particular color when incident on same coloured objects gets reflected without getting absorbed and complimentary color of object gets absorbed by that object.
                                                      
  WORKING:
An rgb led is given input by microcontroller,so that it glows in three colors with a small delay for each colour.during that delay period(of each colour) the LDR's resistance changes accordingly and that data is collected by microcontroller and microcontroller gives HIGH or LOW signal to the other RGB Led,whose colour tells which coloured object is sensed.Here the LDR's values for different colours (red,green, blue) of the first mentioned RGB led(in this text) are recorded and some comparisions are made by microcontroller(mentioned in the below Code) and accordingly output RGB LED glows(gives corresponding colour of object).   
                                                         
  CODE:
/*------------------------------------------------------TRI-colour detector---------------------------------------------------------------------*/
/*here the value of ldr will be recorded and compared for different colored lights incident on object and comparision of those values will be done and accordingly output rgb led colour will glow*/

int redled = 2;

int greenled = 3;

int blueled = 4;

int value = A0;

int red;

//ldr value is recorded for red light incident on object through A0 pin and that value is stored in red variable

int blue;

//similarly for blue and green

int green;

int redvalue;

//based on comparision of above values input to output rgb led is given(high/low) through these variables

int greenvalue;

int bluevalue;

int redout = 8;

//digitals pins of output rgb led(that glows after detecting color)

int blueout = 10;

int greenout = 9;

void setup() 

{

  pinMode(redled, OUTPUT);
  
  pinMode(blueled, OUTPUT);
  
  pinMode(greenled, OUTPUT);
  
  pinMode(value, INPUT);
  
  pinMode(redout, OUTPUT);
  
  pinMode(blueout, OUTPUT);
  
  pinMode(greenout, OUTPUT);
  
  Serial.begin(9600);
  
}

void loop()

{
  digitalWrite(redled, LOW);
  
  //here the two rgb leds used are common cathode type so when LOW is given rgb led glows and dims when HIGH is given
  
  delay(20);
  
  red = analogRead(value);
  
  delay(5);
  
  Serial.print("R=");
  
  Serial.println(red);
  
  digitalWrite(redled, HIGH);

  digitalWrite(greenled, LOW);
  
  delay(20);
  
  green = analogRead(value);
  
  delay(5);
  
  Serial.print("G=");
  
  Serial.println(green);
  
  digitalWrite(greenled, HIGH);

  digitalWrite(blueled, LOW);
  
  delay(20);
  
  blue = analogRead(value);
  
  delay(5);
  
  Serial.print("B=");
  
  Serial.println(blue);
  
  digitalWrite(blueled, HIGH);

  if (red > green && red > blue)
  
  { 
    redvalue = LOW;
  }
  
  else
    redvalue = HIGH;

  if (red < green && green > blue)
  
  { 
    greenvalue = LOW;
  }
  else
    greenvalue = HIGH;

  if (blue > green && red < blue)
  
  { 
    bluevalue = LOW;
  }
  else
    bluevalue = HIGH;

  digitalWrite(redout, redvalue);
  
  digitalWrite(greenout, greenvalue);
  
  digitalWrite(blueout, bluevalue);

}
