
# Registers

### Ports 
PORTx - used for setting a value
- Port B - The last 6 Digital Pins (8-13) (PB0 -> 8, PB1 -> 9, PB2 -> 10)
- Port C - Analog Pins (PC0, PC1, PC2)
- Port D - First 8 Digital Pins (0-7) (PD0, PD1, PD2)

Correct way of setting up a HIGH value: 
PORTB |= B00001000

this way if PORTB is = B10100000, the value of the new PORTB will be B10101000

Correct way of setting up a LOW value: 
PORTB &= B11110111 
OR 
PORTB &= !B00001000 

### Data Direction Register (DDR)
defines a port as output or input (0 - Output, 1 - Input)
- DDRB
- DDRC
- DDRD

![[Pasted image 20241215104340.png]]


### PINx - The Port X Input Pins Address
Stores the Input value of each pin on each port

![[Pasted image 20241215105247.png]] 
**In the given image the result is shifted with 5 bits because we want a value that is either 1 or 0**

![[Pasted image 20241215105355.png]]

# Pin Change Interruptions  (Hardware Interruptions)
### PCICR - Pin Cahnge Interrup Control Register

setting a one of the following to 1 means that the pin WILL trigger interruptions on change. On zero it won't.

Bit 0 - PCIE0 - GROUP 0 - Port B
Bit 1 - PCIE1 - GROUP 1 - Port C
Bit 2 - PCIE2 - GROUP 2 - Port D

PCMSK - Pin Change Mask Register
PCINT bits are controller by the PCMSK Register


![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc5cxD1nLVRBXqxFcycgfepK7pxMveVxiKSBnRCiy_UJIrN9xjLoVn4r5dVSg3__da_64EAvQmW9PTwZcwk-ivev1K8Pxqn5oOAUywic7I0HQ4ksyhgR1uxbI7ysg4a0XUqkZR3JjaOf9QLkwJh8af08tVA?key=0nwzroylsV60eVu13suPOA)
![[Pasted image 20241215130903.png]]![[Pasted image 20241215131557.png]]

# Timers
3 timers - Timer 1, 2, 3

### Timer Register

- pre-scaler
	- on timer 0 and 2 -> 8 bit - 0 to 255
	- on timer 1 -> 16 bit - 0 to 65k

## Timer Interrupts
- Compare match - matches the value of the timer (for example 100 and when the timer is equal to 100 it triggers the interruption)
- Overflow - interruption is triggered once the maximum value is reached
- Input Capture - only on timer 1 -> the value of the timer can be stored in a different register, each time an external event happens (on one of the Arduino pins)

**Used by means that the specific functions on the pins might stop working**
![[Pasted image 20241215164434.png]]

### TCCRxA and TCCRxB
x is the number of the timer

- TCCRA register controls the PWM mode
- TCCRB - using for a pre-scaler value