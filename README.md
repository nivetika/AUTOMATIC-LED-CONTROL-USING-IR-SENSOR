# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/ea5626ba-1c18-42ce-a461-e7b0cdef910b" />


2. Click **File → New STM32 Project**.
   <img width="1920" height="1200" alt="Screenshot (51)" src="https://github.com/user-attachments/assets/d51e735c-213a-4387-8e9e-4847fcaab8ed" />

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/dd9d241d-dc35-415c-8664-6cf733bd4eb5" />


3. Select the **target microcontroller** or board and click **Next**.
  <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/e1ecddd0-2be4-4710-a84d-4709c4bfdc87" />

4. Name the project.
   
   <img width="595" height="660" alt="image" src="https://github.com/user-attachments/assets/fd52b8ab-f949-4079-ac51-7039c3011f98" />


5. The corresponding `.ioc` file will be generated automatically.
   
   <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/91d117d9-cfbe-4f78-8158-a2823240c4e8" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   
  <img width="1920" height="1200" alt="Screenshot (56)" src="https://github.com/user-attachments/assets/4e03951a-914e-41b1-9112-ffc4ff90f85d" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
    
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/2e0d929e-59ae-4de4-b67f-edff5b19fdfd" />

 
8. Edit the generated main program as required.
   
   <img width="1920" height="1200" alt="Screenshot (58)" src="https://github.com/user-attachments/assets/4bf00ac8-af44-43aa-899c-b52dbd488485" />


9. Click **Project → Build All**.

	<img width="1920" height="1200" alt="Screenshot (59)" src="https://github.com/user-attachments/assets/775dfe87-3ba4-4ad1-a9ee-0bd83b3c63ee" />


10. Link the **HEX file** using the post-build process.

   <img width="721" height="274" alt="image" src="https://github.com/user-attachments/assets/2a906baf-018d-48e6-93f4-f768c85743c9" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    
    <img width="1919" height="1196" alt="image" src="https://github.com/user-attachments/assets/5b64af4c-1b08-402f-bd93-1d15adf132c7" />


12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-10-29 at 16 17 32_a0f89cf4](https://github.com/user-attachments/assets/3e3eacc8-e3d3-4ec6-b30a-082aa3282317)


CASE 2: LED OFF

![WhatsApp Image 2025-10-29 at 16 17 49_56c29caf](https://github.com/user-attachments/assets/8299d29f-d40e-48d1-be1a-83c0535341dd)


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




