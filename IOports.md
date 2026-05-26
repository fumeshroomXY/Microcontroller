# I/O port
An I/O port is simply a **hardware register** inside a peripheral, such as:

- GPIO direction register

- UART transmit register

- Timer control register

- ADC result register

These registers control or report the state of the peripheral.

So an I/O port is **the thing you want to access**.


# Mapped I/O
Microcontrollers need a way for the CPU to communicate with peripherals (timers, UART, GPIO, ADC, etc.). 

There are two major approaches:

## Memory‑Mapped I/O
Peripherals are **assigned addresses in the same address space as RAM and ROM**.

- The CPU treats peripheral registers as if they were memory.
- Reading/writing uses **normal load/store instructions**.

Example:
```c
*(volatile uint32_t*)0x40021000 = 1;   // write to GPIO register
```

Used by
- ARM Cortex‑M (STM32, nRF, LPC, etc.)
- RISC‑V MCUs
- Many 32‑bit microcontrollers

#### Advantages
- Simple instruction set (no special I/O instructions)

- Uniform addressing model

- Easy for compilers

#### Disadvantages
- Uses up part of the memory address space
- Needs careful protection to avoid accidental writes

## I/O‑Mapped I/O
Peripherals live in a **separate I/O address space**, not in memory.

- CPU has **special instructions** for I/O.

Example:
```markdown
IN  AL, 0x60
OUT 0x64, AL
```

Used by
- **x86 processors**
- Some older 8‑bit MCUs (Z80, 8085)

#### Advantages
- Memory address space is preserved
- Clear separation between memory and I/O

#### Disadvantages
- Requires special instructions
- More complex for compilers
