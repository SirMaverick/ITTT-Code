# ITTT-Code

#include "Pitches.h"
int Button = 6;
int Buzzer = 9;
int Trans1 = A0;
int Trans2 = A1;
int Trans3 = A2;
int Trans4 = A3;
int Trans5 = A4;
int Trans6 = A5;
int LastNote = 0;
int LastState = 0;
int State = 0;
int NoteDuration = 40;
int List;
int Note1 = NOTE_C5;
int Note2 = NOTE_D5;
int Note3 = NOTE_E5;
int Note4 = NOTE_F5;
int Note5 = NOTE_G5;
int Note6 = NOTE_A5;
int Value1 = 0;
int Value2 = 0;
int Value3 = 0;
int Value4 = 0;
int Value5 = 0;
int Value6 = 0;
int LED1 = 12;
int LED2 = 11;
int LED3 = 8;
int LED4 = 7;
int LED5 = 4;
int LED6 = 2;
int Playlist[] = {};
int NotesPlayed1 [] = {Note6, Note6, Note6, Note4, Note6, NOTE_C6, Note1} ;
int NotesPlayed[] = {Note1, Note2, Note3, Note1, Note1, Note2, Note3, Note1, Note3, Note4, Note5, Note3, Note4, Note5, Note5, Note6, Note5, Note4, Note3, Note1, Note5, Note6, Note5, Note4, Note3, Note1, Note1, Note1};
int x = 0 ;
int y = 0 ;
int ButtonState = 0;
int LastButtonState = LOW;

void setup() {
  Serial.begin(9600);
  pinMode(Buzzer, OUTPUT);
  pinMode(Trans1, INPUT);
  pinMode(Trans2, INPUT);
  pinMode(Trans3, INPUT);
  pinMode(Trans4, INPUT);
  pinMode(Trans5, INPUT);
  pinMode(Trans6, INPUT);
  pinMode(LED1, OUTPUT);
  pinMode(LED2, OUTPUT);
  pinMode(LED3, OUTPUT);
  pinMode(LED4, OUTPUT);
  pinMode(LED5, OUTPUT);
  pinMode(LED6, OUTPUT);
  pinMode(Button, INPUT);
}

void loop() {
  Serial.print("Reading = ");
  Serial.println(Value4);
  if (y == 0){ 
    Note1 = NOTE_C5;
    Note2 = NOTE_D5;
    Note3 = NOTE_E5;
    Note4 = NOTE_F5;
    Note5 = NOTE_G5;
    Note6 = NOTE_A5;
  } else if (y == 1){
    Note1 = NOTE_C6;
    Note2 = NOTE_D6;
    Note3 = NOTE_A4;
    Note4 = NOTE_B4;
    Note5 = NOTE_D5;
    Note6 = NOTE_E5;
  } else if (y > 1) {
    y = 0;
  }
  ButtonState = digitalRead(Button);
  Value1 = analogRead(Trans1);
  Value2 = analogRead(Trans2);
  Value3 = analogRead(Trans3);
  Value4 = analogRead(Trans4);
  Value5 = analogRead(Trans5);
  Value6 = analogRead(Trans6);
  if ( ButtonState == HIGH) {
    if (LastButtonState != ButtonState) {
      y++;
      LastButtonState = HIGH;
    }
   } else {
    LastButtonState = LOW;
  }
  if (NotesPlayed[x] == Note1 and LastState == 0) {
    digitalWrite(LED1, HIGH);
  } else if (NotesPlayed[x] == Note2 and LastState == 0) {
    digitalWrite(LED2, HIGH);
  } else if (NotesPlayed[x] == Note3 and LastState == 0) {
    digitalWrite(LED3, HIGH);
  } else if (NotesPlayed[x] == Note4 and LastState == 0) {
    digitalWrite(LED4, HIGH);
  } else if (NotesPlayed[x] == Note5 and LastState == 0) {
    digitalWrite(LED5, HIGH);
  } else if (NotesPlayed[x] == Note6 and LastState == 0) {
    digitalWrite(LED6, HIGH);
  }
  if (Value1 > 200) {
    tone(Buzzer, Note1, NoteDuration);
    State = 1;
    if (NotesPlayed[x] == Note1 and State == 1 and LastState == 0) {
      digitalWrite(LED1, LOW);
      if (LastState != State) {
        x++ ;
        LastState = 1;
      }
    } 
  } else if (Value1 < 100) {
      LastState = 0;
  }
  if (Value2 > 200) {
    tone(Buzzer, Note2, NoteDuration);
    State = 1;
    if (NotesPlayed[x] == Note2 and State == 1 and LastState == 0) {
      digitalWrite(LED2, LOW);
      if (LastState != State) {
        x++ ;
        LastState = 1;
      }
    } 
  } else {
    LastState = 0;
  }
  if (Value3 > 200) {
    tone(Buzzer, Note3, NoteDuration);
    State = 1;
    if (NotesPlayed[x] == Note3 and State == 1 and LastState == 0) {
      digitalWrite(LED3, LOW);
      if (LastState != State) {
        x++ ;
        LastState = 1;
      }
    } 
  } else {
    LastState = 0;
  }
    if (Value4 > 200) {
    tone(Buzzer, Note4, NoteDuration);
    State = 1;
    if (NotesPlayed[x] == Note4 and State == 1 and LastState == 0) {
      digitalWrite(LED4, LOW);
      if (LastState != State) {
        x++ ;
        LastState = 1;
      }
    } 
  } else {
    LastState = 0;
  }
  if (Value5 > 200) {
    tone(Buzzer, Note5, NoteDuration);
    State = 1;
    if (NotesPlayed[x] == Note5 and State == 1 and LastState == 0) {
      digitalWrite(LED5, LOW);
      if (LastState != State) {
        x++ ;
        LastState = 1;
      }
    } 
  } else {
    LastState = 0;
  }
  if (Value6 > 200) {
    tone(Buzzer, Note6, NoteDuration);
    State = 1;
    if (NotesPlayed[x] == Note6 and State == 1 and LastState == 0) {
      digitalWrite(LED6, LOW);
      if (LastState != State) {
        x++ ;
        LastState = 1;
      }
    } 
  } else {
    LastState = 0;
  }
}
