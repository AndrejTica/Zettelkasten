---
date: 2025-11-24
tags:
  - microcontroller 
---
There are 3 factors when calculating the timer interrupt period:
- Input clock frequency
- Timer prescaler (PSC)
- Auto-reload value (ARR)

### Timer input clock
Not always the same as the core clock. Each timer tits on a bus (APB1 or APB2). Each APB has its own prescaler.

### Timer prescaler (PSC)
The timer has a 16-bit PSC register.

$$
F_{timer} = \frac{F_{clk}}{PSC + 1}
$$

Why + 1? Because both the PSC and ARR are defined as "one less than what you think". The hardware counts from 0 up to the register value, 
so the number of ticks is value + 1.

### Auto-reload value (ARR)
The ARR sets when the counter overflows (update event), which is what triggers the interrupt. 
- In up-counting mode, the counter goes from 0 to ARR, then rolls over.

### Final formula to calculate the interrupt period
$$
T_{interrupt} = \frac{ARR + 1}{F_{timer}} = \frac{(PSC+1)(ARR+1)}{T_{timer}}
$$

### Resolution vs range
The tick frequency is the time resolution:
- Smaller prescaler -> higher Ftimer -> better resolution, but smaller maximum period for given ARR.
- Larger prescaler -> lower Ftimer -> worser resolution, but longer max period. 

Lower resolution means that the smallest time step is big, and that can break or degrade anything that needs finer timer timing. 
So choose smallest possible prescaler value. 
