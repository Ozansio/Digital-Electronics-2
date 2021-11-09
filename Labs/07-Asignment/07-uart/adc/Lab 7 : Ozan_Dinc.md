
# Lab 7: Ozan_Dinc


https://github.com/Ozansio/Digital-Electronics-2/new/main/Labs/07-Asignment/07-uart/adc

1.Complete table with voltage divider, calculated, and measured ADC values for all five push buttons.

![image](https://user-images.githubusercontent.com/91128854/140883909-17f0d7bc-c51b-4dd0-a830-479ef0b80841.png)

Code listing of ACD interrupt service routine for sending data to the LCD/UART and identification of the pressed button. Always use syntax highlighting and meaningful comments:

/**********************************************************************
 * Function: ADC complete interrupt
 * Purpose:  Display value on LCD and send it to UART.
 **********************************************************************/
```c
/**********************************************************************
 * Function: ADC complete interrupt
 * Purpose:  Display value on LCD and send it to UART.
 **********************************************************************/
ISR(ADC_vect)
{
    uint16_t value = 0;
    char lcd_string[4] = "0000";

    value = ADC;                  // Copy ADC result to 16-bit variable
    itoa(value, lcd_string, 10);  // Convert decimal value to string

    // WRITE YOUR CODE HERE
  //Clear previous value
    lcd_gotoxy(8,0);
    lcd_puts("    ");
    //Put new value TO LCD
    itoa(value, lcd_string, 10);  // Convert decimal value to string
    lcd_gotoxy(8,0);
    lcd_puts(lcd_string);
    // send the same value to UART
     uart_puts(lcd_string);
     uart_puts(" ");
     
     
    //Clear previous value
    lcd_gotoxy(13,0);
    lcd_puts("    ");
    //Put new value to LCD
    
    //display value in hexa
    itoa(value, lcd_string, 16);  // Convert decimal value to string
    lcd_gotoxy(13,0);
    lcd_puts(lcd_string);
    
    //display what button was pressed
     lcd_gotoxy(8,1);
     lcd_puts("    ");
     lcd_gotoxy(12,1);
     lcd_puts("    ");
    
    
     lcd_gotoxy(8, 1);
     itoa(value, lcd_string, 10);
     if (value>1000) { lcd_puts("none");}
         if ((value>600)&&(value<1000)) { lcd_puts("select");}
              if ((value>350)&&(value<450)) { lcd_puts("left");}
                   if ((value>200)&&(value<270)) { lcd_puts("down");}
                        if ((value>5)&&(value<120)) { lcd_puts("up");}
                             if (value==0) { lcd_puts("right");}
             
     // lcd_puts(lcd_string);
;

}
```

1.UART communication
(Hand-drawn) picture of UART signal when transmitting three character data De2 in 4800 7O2 mode (7 data bits, odd parity, 2 stop bits, 4800 Bd).
![sinyaller](https://user-images.githubusercontent.com/91128854/140888624-6ea92158-5119-40e4-8bc0-ca14c9849c2f.jpeg)


2. Flowchart figure for function `uint8_t get_parity(uint8_t data, uint8_t type)` which calculates a parity bit of input 8-bit `data` according to parameter `type`. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

![schema](https://user-images.githubusercontent.com/91128854/140888575-8b6ef4c7-d434-44b0-a737-fe1eccee0bef.jpeg)

### Temperature meter

Consider an application for temperature measurement and display. Use temperature sensor [TC1046](http://ww1.microchip.com/downloads/en/DeviceDoc/21496C.pdf), LCD, one LED and a push button. After pressing the button, the temperature is measured, its value is displayed on the LCD and data is sent to the UART. When the temperature is too high, the LED will start blinking.

1. Scheme of temperature meter. The image can be drawn on a computer or by hand. Always name all components and their values.
![adli](https://user-images.githubusercontent.com/91128854/140888449-39e86908-a7dd-4645-88cf-316ed44d4008.jpeg)













