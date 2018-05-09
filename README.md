# arduino_barcode128
Generates a String representation of a Barcode (code 128)



## Example of use

    #include <Barcode.h>
    Barcode barcode;
    // (...)
    void drawBarcode(String text)
    {
    //Call barcode.make with desired string to codify
      String bars = barcode.make(text);
      // Input -> 11648
      // Output -> "211412123221123221223112221231311222132212233111"
      // Each number is a bar length, alternating Black / White
      
      //Goes through retrieved string, drawing the bars
      for (int i = 0; i < bars.length(); i++){
          int barLen = bars[i] - '0';
          int startBar = posBar;
          posBar+= barLen;
          if (i%2 == 0) {
            display.fillRect(0, startBar, 45, posBar, GxEPD_BLACK);      
          } else {
            display.fillRect(0, startBar, 45, posBar, GxEPD_WHITE);
          }          
      }
      display.updateWindow(0, 0, 45, display.height(), false)
    }
