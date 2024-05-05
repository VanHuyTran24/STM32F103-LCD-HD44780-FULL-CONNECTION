# STM32 library for FULL CONNECTION HD44780 LCD

## Demo
```
#include "main.h"
#include "TranVanHuy_LCD.h"


#include <stdio.h>
struct _FILE
{
	int handle;
};
FILE __stdout;
int fputc(int ch, FILE *f) 
{
	LCD_putchar(ch);
  return ch;
}

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{

  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
	
	LCD_init();
	const uint8_t CGRAM0[] = {0x0,0xA,0x1F,0x1F,0x1F,0xE,0x4,0x0}; // <3
	const uint8_t CGRAM1[] = {0x0,0xA,0x0,0x0,0x11,0xE,0x0,0x0}; // :)
	const uint8_t CGRAM2[] = {0xE,0x9,0x9,0x1D,0x9,0x9,0xE,0x0}; // "Đ"
	
	LCD_setCGRAM((uint8_t *)CGRAM0,0);
	LCD_setCGRAM((uint8_t *)CGRAM1,1);
	LCD_setCGRAM((uint8_t *)CGRAM2,2);
	
	
	LCD_gotoXY(0,0);
	LCD_printf((uint8_t *)"\2H SPKT TP.HCM\n\r",'\r');
	printf("C\2T 2023");
	LCD_putchar(0);
	LCD_putchar(1);
  while (1)
  {

  }

}

```
![image](https://github.com/VanHuyTran24/STM32F103-LCD-HD44780-FULL-CONNECTION/assets/166670555/bfff8c71-8ed3-4464-b153-cf9a9914c31e)

## Library
Download Library File (.c) from [here](https://github.com/VanHuyTran24/STM32F103-LCD-HD44780-FULL-CONNECTION/blob/master/Program_KeilC/MDK-ARM/TranVanHuy_LCD.c)
