
## Zad. 1
```cpp
const int buzzer = 8; //WPISZ PIN GLOSNIKA
const int przycisk = 2; //WPISZ PIN PRZYCISKU
const int OUTPUT_LED_PIN = LED_BUILTIN;


void setup(){

    //Ustaw pinMode - wejście (input) czy wyjście (output)?
    pinMode(buzzer, OUTPUT);
    pinMode(przycisk, INPUT);

    //Wypisywanie informacji w konsoli
    Serial.begin(9600);

}

void loop(){


    //odcztaj wartosc z przycisku za pomoca digitalRead()
    int wcisniety = digitalRead(przycisk);

    //Prosty sygnal dzwiekowy przez jedna sekunde
    if(wcisniety == 1){
        tone(buzzer, 432); 
        delay(1000); 
        tone(buzzer, 2000); 
        delay(2000);      
        noTone(buzzer);   
        delay(1000);         
    }

    /*
        Zmodyfikuj powyzszy kod na sygnal: 
        - 432 HZ przez 1 sekunde
        - sekunda ciszy
        - 2000 HZ przez 2 sekundy
    */
}
```

## Pianino cale
```cpp
/*
 * Demonstrates how to make a simple piano using tactile buttons (for keys) and the
 * tone library with a piezo buzzer (for output)
 * 
 * By Jon E. Froehlich
 * @jonfroehlich
 * http://makeabilitylab.io
 * 
 * For a walkthrough and circuit diagram, see:
 * https://makeabilitylab.github.io/physcomp/arduino/piano
 * 
 * Note: Use of the tone() function will interfere with PWM output on pins 3 and 11 
 * (on boards other than the Mega). See:
 * https://www.arduino.cc/reference/en/language/functions/advanced-io/tone/
 * 
 */

// Frequencies (in Hz) of our piano keys
// From: https://en.wikipedia.org/wiki/Piano_key_frequencies
// Looks like there are also constants built into the tone library
// https://github.com/bhagman/Tone#musical-notes
#define KEY_C 262  // 261.6256 Hz (middle C)
#define KEY_D 294  // 293.6648 Hz
#define KEY_E 330  // 329.6276 Hz
#define KEY_F 350  // 349.2282 Hz
#define KEY_G 392  // 391.9954 Hz
#define KEY_A 440

// I lay out my buttons like piano keys. So, lower frequencies on left
// and increasingly higher frequencies to the right
// Change this depending on how you've laid out your keys
const int INPUT_BUTTON_C_PIN = 6;
const int INPUT_BUTTON_D_PIN = 5;
const int INPUT_BUTTON_E_PIN = 4;
const int INPUT_BUTTON_F_PIN = 3;
const int INPUT_BUTTON_G_PIN = 2;

const int OUTPUT_PIEZO_PIN = 8;
const int OUTPUT_LED_PIN = LED_BUILTIN; // visual feedback on button press

// By default, we assume buttons are in pull-up configurations
// Switch the following to false and change INPUT_PULLUP belows
// to INPUT
const boolean _buttonsAreActiveLow = true; 

void setup() {
  pinMode(INPUT_BUTTON_C_PIN, INPUT_PULLUP);
  pinMode(INPUT_BUTTON_D_PIN, INPUT_PULLUP);
  pinMode(INPUT_BUTTON_E_PIN, INPUT_PULLUP);
  pinMode(INPUT_BUTTON_F_PIN, INPUT_PULLUP);
  pinMode(INPUT_BUTTON_G_PIN, INPUT_PULLUP);
  pinMode(OUTPUT_PIEZO_PIN, OUTPUT);
  pinMode(OUTPUT_LED_PIN, OUTPUT);

  Serial.begin(9600);
}

void loop() {

  // tone() generates a square wave of the specified frequency (and 50% duty cycle) on a pin. 
  // A duration can be specified, otherwise the wave continues until a call to noTone().
  // See: https://www.arduino.cc/reference/en/language/functions/advanced-io/tone/
  // 
  // Check each button to see if they're pressed. If so, play the corresponding note
  // We can only play one tone at a time, hence the massive if/else block
  if(isButtonPressed(INPUT_BUTTON_C_PIN)){
    tone(OUTPUT_PIEZO_PIN, KEY_C);
    Serial.println("2");
  }else if(isButtonPressed(INPUT_BUTTON_D_PIN)){
    tone(OUTPUT_PIEZO_PIN, KEY_D);
       Serial.println("3");
  }else if(isButtonPressed(INPUT_BUTTON_E_PIN)){
    tone(OUTPUT_PIEZO_PIN, KEY_E);
       Serial.println("4");
  }else if(isButtonPressed(INPUT_BUTTON_F_PIN)){
    tone(OUTPUT_PIEZO_PIN, KEY_F);
       Serial.println("5");
  }else if(isButtonPressed(INPUT_BUTTON_G_PIN)){
    tone(OUTPUT_PIEZO_PIN, KEY_G);
       Serial.println("6");
  }else{
    noTone(OUTPUT_PIEZO_PIN); // turn off the waveform
    digitalWrite(OUTPUT_LED_PIN, LOW);
  }
}

boolean isButtonPressed(int btnPin){
  int btnVal = digitalRead(btnPin);
  if(_buttonsAreActiveLow && btnVal == LOW){
    // button is hooked up with pull-up resistor
    // and is in a pressed state
    digitalWrite(OUTPUT_LED_PIN, HIGH);
    return true;
  }else if(!_buttonsAreActiveLow && btnVal == HIGH){
    // button is hooked up with a pull-down resistor
    // and is in a pressed state
    digitalWrite(OUTPUT_LED_PIN, HIGH);
    return true;
  }

  // button is not pressed
  return false;
}

```
