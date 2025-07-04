# 🛠️ RC Car with FlySky FS-i6 | Arduino Controlled

This project implements a **tank-style RC car** controlled via a **FlySky FS-i6 transmitter** and **Arduino Uno**. The vehicle uses differential drive logic—meaning it turns by varying the speeds of the left and right wheels, just like a tank. This eliminates the need for physical steering components and allows for precise pivot turns and smooth directional control.

---

## 🎮 Features

- ✅ **FlySky FS-i6 Receiver** input via `pulseIn()` (PWM)
- ✅ **Tank-style differential drive**
- ✅ Forward/backward with Channel 2 (right stick vertical)
- ✅ Turning left/right with Channel 1 (right stick horizontal)
- ✅ **PWM motor speed control** (`analogWrite`)
- ✅ Safe stop on signal loss
- ✅ Deadzone filtering to ignore joystick noise
- ✅ Compatible with **L298N** or similar H-bridge drivers

---

## ⚙️ Hardware Requirements

| Component             | Details                             |
|----------------------|-------------------------------------|
| Microcontroller       | Arduino Uno / Nano                 |
| Transmitter & Receiver| FlySky FS-i6 + 6CH Receiver        |
| Motor Driver          | L298N Dual H-Bridge                |
| Drive Motors          | 2x DC gear motors                  |
| Power Source          | 2S/3S LiPo or battery pack         |
| Miscellaneous         | Jumper wires, custom chassis       |

---

## 📡 Channel Mapping

| Stick Action        | Function            |
|---------------------|---------------------|
| Forward / Backward  | Throttle (speed)    |
| Left / Right        | Turn (differential) |

> The **right joystick** alone controls both speed and direction.

---

## 🧠 How It Works

1. Reads **PWM signals** from FlySky receiver on pins D4 (CH1) and D6 (CH2).
2. Maps joystick values to speed using Arduino’s `map()` and `analogWrite()`.
3. Implements **tank-style logic**:
   - Both motors forward/backward for straight movement
   - One motor slower or reversed to allow turning
   - Opposite directions for in-place rotation
4. Adds **deadzone logic** to avoid twitching when joystick is near center.
5. On **signal loss** (pulse width out of bounds), it cuts motor power for safety.

---

## 🚀 Getting Started

1. **Wire the Receiver**:
   - CH1 → D4
   - CH2 → D6

2. **Connect the L298N Motor Driver**:
   - ENA, IN1, IN2 → Motor A
   - ENB, IN3, IN4 → Motor B
   - Use PWM pins (e.g., D5, D9)

3. **Upload Arduino Sketch** to your board.

4. **Power Motors** using a separate 7.4V–12V source (not USB).

5. **Control the Car** using the right joystick on your FlySky FS-i6.


