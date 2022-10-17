# EXPERIMENT 04 - INTERFACING A 16X2 TYPE LCD DISPLAY TO LPC2148 ARM 7 MICROCONTROLLER
Name : S.Sumyuktha Rani

Roll no : 212220230050

Date of experiment : 15-10-2022
## Aim: 
To Interface 16X2 type LCD display to LPC2148 ARM 7 and write a code for displaying a string in it.

## Components required:
Proteus ISIS professional suite, Kiel μ vision 5 Development environment

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Theory:
 
## LCD 16X2

![image](https://user-images.githubusercontent.com/36288975/195774401-e3bffb44-0d3d-4b7e-b374-7a7a7ef60d48.png)

![image](https://user-images.githubusercontent.com/36288975/195773232-ab5dd9b0-99b7-4663-9bdf-6665fa93a052.png)

Fig.01 16X2 LCD DISPLAY 

Apart from the voltage supply connections the important pins from the programming perspective are the data lines(8-bit Data bus), Register select, Read/Write and Enable pin.

Data Bus: As shown in the above figure and table, an alpha numeric lcd has a 8-bit data bus referenced as D0-D7. As it is a 8-bit data bus, we can send the data/cmd to LCD in bytes. It also provides the provision to send the the data/cmd in chunks of 4-bit, which is used when there are limited number of GPIO lines on the microcontroller.

Register Select(RS): The LCD has two register namely a Data register and Command register. Any data that needs to be displayed on the LCD has to be written to the data register of LCD. Command can be issued to LCD by writing it to Command register of LCD. This signal is used to differentiate the data/cmd received by the LCD.
If the RS signal is LOW then the LCD interprets the 8-bit info as Command and writes it Command register and performs the action as per the command.
If the RS signal is HIGH then the LCD interprets the 8-bit info as data and copies it to data register. After that the LCD decodes the data for generating the 5x7 pattern and finally displays on the LCD.

Read/Write(RW): This signal is used to write the data/cmd to LCD and reads the busy flag of LCD. For write operation the RW should be LOW and for read operation the R/W should be HIGH.

Enable(EN): This pin is used to send the enable trigger to LCD. After sending the data/cmd, Selecting the data/cmd register, Selecting the Write operation. A HIGH-to-LOW pulse has to be send on this enable pin which will latch the info into the LCD register and triggers the LCD to act accordingly.

<br><br>

## Procedure:
For creation of project on Kiel μ vision 5 Development environment (LPC21 XX/48/38)
1.	Click on the menu Project — New µVision Project creates a new project. Select an empty folder and enter the project name, for example Project1. It is good practice to use a separate folder for each project.
2.	Next, the dialog Select Device for Target opens.
![image](https://user-images.githubusercontent.com/36288975/193398020-d0963a16-4349-4979-87d7-4c9dc11e2346.png)
Figure -01 Target selection
Select the device database. Default is Software Packs. You can have various local device databases, which show up in the drop-down box. For legacy devices (Arm7, Arm9), use the Legacy Device Database [no RTE]
3.	Select the device for your application. This selection defines essential tool settings such as compiler controls, the memory layout for the linker, and the Flash programming algorithms.
4.	Click OK.
5.	Click on the new file option and save the file using save option with .C extension 

For creating the simulation environment in Proteus suite Starting New Design

Step 1: Open ISIS software and select New design in  File menu

![image](https://user-images.githubusercontent.com/36288975/193398023-cb8690cf-914a-47e3-8901-c8db3e4cd223.png)

Figure -02 Proteus File Menu

Step 2: A dialogue box appears to save the current design. However, we are creating a new design file so you can click Yes or No depending on the content of the present file. Then a Pop-Up appears asking to select the template. It is similar to selecting the paper size while printing. For now select default or according to the layout size of the circuit.

![image](https://user-images.githubusercontent.com/36288975/193398027-fd5ae82c-341e-4ed9-aaa4-6bf7574c1a39.png)

Figure -03 Proteus Default Template Select
 
Step 3: An untitled design sheet will be opened, save it according to your wish,it is better to create a new folder for every layout as it generates other files supporting your design. However,it is not mandatory.

![image](https://user-images.githubusercontent.com/36288975/193398031-03ecd6a5-d9b1-4a60-9dee-009c17a3f5dd.png)

Figure -04 Proteus Design Sheet
 
Step 4: To Select components, Click on the component mode button.

![image](https://user-images.githubusercontent.com/36288975/193398044-5e0d1fe6-1d2b-4b54-9c54-f2904b234343.png)

Figure -05 Component Mode

Step 5: Click On Pick from Libraries. It shows the categories of components available and a search option to enter the part name.

![image](https://user-images.githubusercontent.com/36288975/193398047-f1d5f143-7980-45de-99f2-30b3c4bc04d6.png)

Figure -06 Pick from Libraries

![image](https://user-images.githubusercontent.com/36288975/193398058-2519b9d0-a2ca-421f-957d-7507fc7791b8.png)

Figure -07 Keywords Textbox

Step 6: Select the components from categories or type the part name in Keywords text box. Place all the required components and route the wires i.e, make connections. Either selection mode above the component mode or component mode allows to connect through wires. Left click from one terminal to other to make connection. Double right-click on the connected wire or the component to remove connection or the component respectively. Double click on the component to edit the properties of the components and click on Ok.

![image](https://user-images.githubusercontent.com/36288975/193398050-d6d28800-0c5b-4f5c-a77c-227f3336a125.png)

Figure -08 Component Properties Selection

Step 7: Select ARM microcontroller from the library – pick part 

![image](https://user-images.githubusercontent.com/36288975/193398055-587ebd36-4b82-4eaf-837c-f94c3cf2d071.png)
  
Figure -09 LPC2138/48 selection

Step 8: After making necessary connections click on debug.

Step 9: The selected components will appear in the devices list. Select the component and place it in the design sheet by left-click., post which select all the associated components as shown in the circuit diagram below. Example shows selection of push button. Select the components accordingly.

![image](https://user-images.githubusercontent.com/36288975/195773760-d08127c0-b006-4c65-aa75-4ea498597162.png)

Figure -10 Circuit diagram of 16x2 LCD interface with LPC2148/38

![image](https://user-images.githubusercontent.com/36288975/193398065-c12b4984-db8e-40cc-890d-221db1c35b0d.png)

Figure -11 Push Button Selection

Step 10: Select the hex file from the Kiel program folder and import the program in to the microcontroller as shown in figure 12,  debug and if no errors in connections are found, run the VSM simulation to view the output.

![image](https://user-images.githubusercontent.com/36288975/193398071-76df0a57-7e76-4868-9769-c63d220482b8.png)

Figure -12 Hex file for simulation

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Kiel - Program:
```
#include <lpc214x.h>
#include <stdint.h>
#include <stdlib.h>
#include <stdio.h>

void delay_ms(uint16_t j)
{
    uint16_t x,i;
	for(i=0;i<j;i++)
	{
    for(x=0; x<6000; x++);
	}
}

void LCD_CMD(char command)
{
	IO0PIN = ( (IO0PIN & 0xFFFF00FF) | (command<<8) );
	IO0SET = 0x00000040;
	IO0CLR = 0x00000030;
	delay_ms(2);
	IO0CLR = 0x00000040;
	delay_ms(5);
}

void LCD_INIT(void)
{
	IO0DIR = 0x0000FFF0;
	delay_ms(20);
	LCD_CMD(0x38);
	LCD_CMD(0x0C);
	LCD_CMD(0x06);
	LCD_CMD(0x01);
	LCD_CMD(0x80);
}

void LCD_STRING (char* msg)
{
	uint8_t i=0;
	while(msg[i]!=0)
	{
		IO0PIN = ( (IO0PIN & 0xFFFF00FF) | (msg[i]<<8) );
		IO0SET = 0x00000050;
		IO0CLR = 0x00000020;
		delay_ms(2);
		IO0CLR = 0x00000040;
		delay_ms(5);
		i++;
	}
}

void LCD_CHAR (char msg)
{
		IO0PIN = ( (IO0PIN & 0xFFFF00FF) | (msg<<8) );
		IO0SET = 0x00000050;
		IO0CLR = 0x00000020;
		delay_ms(2);
		IO0CLR = 0x00000040;
		delay_ms(5);
}

int main(void)
{
	uint8_t j;
	char val_j[3];
	j = 0;
	
	LCD_INIT();
	LCD_STRING("19EE309");
	LCD_CMD(0xC0);
	LCD_STRING("ARM");

	return 0;
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Output: 

![EXPT4](https://user-images.githubusercontent.com/75235818/196092607-85ea0d1c-8a2e-4187-8ef3-ae5e4960165b.png)

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

###  Circuit Diagram:

![EXPT4-1](https://user-images.githubusercontent.com/75235818/196092638-2d63142b-e611-4b5d-883c-75b69ad691b7.png)

## Result :
Thus, Interfacing an LCD with ARM microcontroller is executed successfully and displayed the strings.
