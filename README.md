# Graph-plotter
Plot voltage vs Time graph from Arduino data


int pin=A0;
char t;
int opin=13;
void setup() {
  Serial.begin(9600);   //Set the baud rate of the comunication
  pinMode(pin,INPUT); 
  pinMode(opin,OUTPUT);
  // put your setup code here, to run once:

}

void loop() {
  if(Serial.available()>0)
  {
    t=Serial.read();
  }
  if(t=='1')
  {
    digitalWrite(opin,HIGH);
  }
  if(t=='0')
  {
    digitalWrite(opin,LOW);
  }
  byte val = map(analogRead(pin),0,1024.0,0,255);//converts analog data to acceptable range
  Serial.write(val);//sends one byte of data at a time
  delay(400);
}
