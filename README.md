# GUINOO_BCA188_Laboratory8

## 1. Pin Table

| Signal | GPIO Used |
|---|---:|
| UART TX | 17 |
| UART RX | 18 |
| I²C SDA | 21 |
| I²C SCL | 20 |
| SPI SCK | 12 |
| SPI MOSI | 11 |
| SPI MISO | 13 |
| SPI CS | 10 |
- **UART Loopback** – Tests UART communication by transmitting and receiving data.
- **I²C Scanner** – Detects connected I²C devices and displays their addresses.
- **SPI Loopback** – Tests SPI communication by sending and receiving data.
  
## 2. Circuit Diagram

The following diagram shows the wiring connections for the ESP32-S3 and the communication interfaces used in this laboratory activity.

<img width="2000" height="1414" alt="LED 1 (pink)" src="https://github.com/user-attachments/assets/8618b792-cf6c-4a0f-8035-4e5a1457918c" />
Figure 1. UART Loopback Circuit Diagram

<img width="2000" height="1414" alt="LED 1 (pink) (1)" src="https://github.com/user-attachments/assets/fd48ba35-a728-4d2e-bd7c-60b8a9cabf2b" />
Figure 2. I²C Scanner Circuit Diagram

<img width="2000" height="1414" alt="LED 1 (pink) (2)" src="https://github.com/user-attachments/assets/58237dfa-732e-4392-9734-13845ef465d0" />
Figure 3. SPI Loopback Circuit Diagram

## 3. Serial Monitor Outputs
### • UART with Jumper Wires
<img width="1535" height="861" alt="d439ae01-9a10-4187-9530-587a6a09fc20" src="https://github.com/user-attachments/assets/90922ee0-4579-40bc-8584-c5e41d5138cc" />
- UART Loopback Serial Monitor Output (PING received successfully)

### • UART without Jumper Wires
<img width="1535" height="862" alt="580c7d84-6b6b-449f-84c8-28e18d20c07d" src="https://github.com/user-attachments/assets/663abb0e-e276-43f6-aa6d-7e0aaaefe94e" />

### • I²C with Module 
<img width="1535" height="862" alt="c9e32786-dd69-4efd-9caf-4763179961fe (1)" src="https://github.com/user-attachments/assets/647a2ae4-c9c8-47fb-a8de-a428ad529f32" />
- I²C Scanner Serial Monitor Output showing a detected device at address 0x3C

### • I²C without Module
<img width="1532" height="839" alt="eafff729-aa8a-40f0-9589-c2473ea140de" src="https://github.com/user-attachments/assets/5ca7ef42-af2c-4329-98cc-661d4cd8ee7e" />
- I²C Scanner Serial Monitor Output showing no I²C devices detected when the module is disconnected

### • SPI with Jumper Wires
<img width="1535" height="838" alt="20387c42-56ad-4347-9bc9-935b925462dc" src="https://github.com/user-attachments/assets/feeffcd0-7a13-460d-9935-1c2687818055" />
- SPI Loopback Serial Monitor Output showing successful data transmission and reception (0xA5)

### • SPI without Jumper Wires
<img width="1535" height="862" alt="5f8f64c2-ae63-4ac5-a115-b114a74dd31d" src="https://github.com/user-attachments/assets/608fa2dc-8f66-4c78-9881-612094edff78" />
- SPI Loopback Serial Monitor Output showing received values of 0xFF and 0x00 without jumper wires

### • Sketch at 9600, monitor at 115200 (UART Loopback)
<img width="1261" height="858" alt="dafa0560-1295-45ee-af0f-191291583749" src="https://github.com/user-attachments/assets/1d2093a6-449e-46d0-9367-1d56bfcd2479" />
- The UART Loopback Serial Monitor Output shows unreadable characters

### • Sketch at 9600, monitor at 9600 (UART Loopback)
<img width="1259" height="912" alt="5ee5dbf9-2810-48ee-b47e-8272dbbcab37" src="https://github.com/user-attachments/assets/e779d56b-63f5-4aa5-b6fc-89f650a3a1c4" />
- The UART Loopback Serial Monitor Output shows repeated “PING” messages

## 4. Expected vs Observed

| Test | Expected | Observed |
|---|---|---|
| UART with jumper | PING received | PING received successfully |
| UART without jumper | No data received | No PING received |
| I2C with module | Device detected | Device detected at 0x3C |
| I2C without module | No device detected | No I2C device found |
| SPI with jumper | Data received correctly (0xA5) | 0xA5 received successfully |
| SPI without jumper | Incorrect data received | 0xFF and 0x00 received |
| Sketch at 9600, monitor at 115200 | Unreadable output | Unreadable characters appeared |
| Sketch at 9600, monitor at 9600 | Readable output | Repeated PING messages appeared |

## 5. Questions

1. Why does UART need both sides to use the same baud rate, while SPI uses a clock line?
   - UART needs the same baud rate so both sides can send and receive data at the correct speed. SPI uses a clock line to control when data is sent and received.
2. Why can two devices with the same address not share one I²C bus?
   - Two devices with the same address can cause conflicts because the controller cannot easily tell which device is responding. Each device should have a unique address on the same I²C bus.
3. Why is CS set HIGH between SPI transfers?
   - CS is set HIGH to deselect the SPI device after a transfer. This prevents the device from responding to data meant for another device.
