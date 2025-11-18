# STM32 FreeRTOS Practice Project

This project demonstrates how to use **FreeRTOS** on an **STM32F4 Series MCU** (tested on STM32F401/STM32F411/STM32F446 boards). It includes basic multitasking examples such as LED blinking and UART serial printing using **CMSIS-RTOS v2 API**.

## 🚀 Features

* FreeRTOS CMSIS-RTOS v2 integration
* LED Task (blinking with delay)
* UART Serial Print Task
* Independent task priorities
* STM32Cube HAL drivers
* Ready for expansion (Queues, Semaphores, Mutexes)

## 🛠️ Development Setup

### **Hardware Requirements**

* STM32 Nucleo board / Discovery board (F4 series preferred)
* USB cable

### **Software Requirements**

* **STM32CubeIDE** (Recommended)
* ARM GCC Toolchain (Auto-installed with CubeIDE)
  
## 📂 Project Structure

ProjectRoot/
 ├── Core/
 │   ├── Inc/
 │   ├── Src/
 │   │   ├── main.c
 │   │   ├── freertos.c
 │   │   ├── stm32f4xx_it.c
 │   │   └── ...
 ├── Middlewares/
 │   └── Third_Party/FreeRTOS/


## 🔧 How to Build & Flash

### **1. Open the project in CubeIDE**

* Go to **File → Open Projects from Filesystem**
* Select your project folder
* Build project (Ctrl+B)

### **2. Flash the firmware**

* Connect board via USB
* Click **Run → Debug** or **Run → Run**

## 🎯 How FreeRTOS Works Here

### **Task Creation**

Tasks are created inside:

MX_FREERTOS_Init();

Using CMSIS-RTOS v2 API:

osThreadNew(Task_LED, NULL, &LED_attributes);
osThreadNew(Task_Serial, NULL, &Serial_attributes);

### **LED Task Example**

void Task_LED(void *argument) {
    while (1) {
        HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
        osDelay(500);
    }
}

### **Serial Task Example**

void Task_Serial(void *argument) {
    char msg[] = "Hello from FreeRTOS!\r\n";
    while (1) {
        HAL_UART_Transmit(&huart2, (uint8_t*)msg, strlen(msg), 100);
        osDelay(1000);
    }
}

## 🧐 Understanding Task Priorities

FreeRTOS runs **higher priority tasks first**.

## 🧪 Future Enhancements

You can extend this project by adding:

* Queues for inter-task communication
* Mutex for UART resource protection
* Binary semaphore for external interrupts
* Software timers
* Event groups

## 📄 License

This project is released under the **MIT License** (included in this repository).

## 👤 Author

**Priyanka G**
