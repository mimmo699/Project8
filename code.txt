// C++ code
//
int piezo = 9;
int switches = A0;

void setup()
{
  pinMode(switches, INPUT);
  pinMode(piezo, OUTPUT);
  Serial.begin(9600);
  
}

void loop()
{
  int signal = analogRead(switches);
  Serial.println(signal);
  
  int array[] = {200, 400, 600, 800};
  
  if(signal == 1023){
    tone(piezo, array[0]);
  }
  else if(signal >= 500 && signal <= 551){
    tone(piezo, array[1]);
  }
  else if(signal == 552 && signal >= 600){
    tone(piezo, array[2]);
  }
  else if(signal == 650){
    tone(piezo, array[3]);
  }
  else {
    noTone(piezo);
  }
}