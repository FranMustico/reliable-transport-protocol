# Reliable Transport Protocol

A simple implementation of the Go-Back-N (GBN) protocol for reliable data transfer, designed as part of a computer networks project. This program simulates the behavior of a transport layer protocol, handling packet transmission, acknowledgment, and retransmission in the presence of packet loss and corruption.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [How It Works](#how-it-works)
- [Usage](#usage)
- [Development](#development)
- [License](#license)

---

## Overview

This project implements the Go-Back-N protocol, a sliding window protocol for reliable data transfer. It is designed to simulate unidirectional data transfer from sender (Entity A) to receiver (Entity B) over an unreliable network. The program handles packet loss, corruption, and retransmission.

---

## Features

- **Go-Back-N Protocol**: Implements a sliding window mechanism for efficient data transfer.
- **Error Detection**: Uses checksums to detect corrupted packets.
- **Retransmission**: Handles retransmission of lost or corrupted packets.
- **Simulation Environment**: Includes a network emulator to simulate packet loss, corruption, and delays.

---

## How It Works

1. **Sender (Entity A)**:
   - Buffers messages from the application layer.
   - Sends packets within the window size.
   - Starts a timer for the first packet in the window.
   - Retransmits all packets in the window upon timeout.

2. **Receiver (Entity B)**:
   - Accepts packets in order.
   - Sends cumulative acknowledgments for correctly received packets.
   - Ignores out-of-order or corrupted packets.

3. **Network Emulator**:
   - Simulates packet loss, corruption, and delays.
   - Delivers packets to the appropriate entity (A or B).

---

## Usage

### Pre-packaged Release

A zip file containing the source code and a precompiled executable (`proj2.exe`) has been prepared for your convenience. You can find it in the **Releases** section of this repository.

To use it:

1. **Download and Extract**:
   - Navigate to the **Releases** section of this repository.
   - Download the zip file.
   - Extract the contents to a directory of your choice.

2. **Run the Executable**:
   - Locate the `proj2.exe` file in the extracted folder.
   - Double-click the executable to launch the program.

   Running the executable will start the simulation and prompt you to enter the required parameters.

---

## Development

### Key Functions

- **Sender (Entity A)**:
  - `A_output()`: Buffers and sends messages.
  - `A_input()`: Processes acknowledgments.
  - `A_timerinterrupt()`: Handles retransmissions on timeout.
  - `A_init()`: Initializes sender state.

- **Receiver (Entity B)**:
  - `B_input()`: Processes incoming packets.
  - `B_init()`: Initializes receiver state.

### Network Emulator

The emulator simulates:

- Packet loss and corruption.
- Timer interrupts for retransmissions.
- Message arrivals from the application layer.

### Compilation

To compile the program, use the following command:

```bash
gcc -Wall -o proj2 proj2.c
```

This will enable all compiler warnings and create an executable named `proj2`.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
