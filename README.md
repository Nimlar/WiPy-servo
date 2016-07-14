# WiPy servo

Simple library to control servos using a WiPy.
It takes care of using the right timer, channel and pin alt function for a given PWM GPIO pin.
On top of that it performs the duty cycle for a timer to rotate a servo to a desired angle.

For example, you can set the angle to 45 degrees for a servo connected to pin 9 using:

```python
desired_angle = 45  # deg
servo_pin = 9  # GP pin

# Servo specific constants
PULSE_MIN = 900  # in µs
PULSE_MAX = 2100  # in µs
FREQUENCY = 50  # Hz
ROTATIONAL_RANGE_100 = 12000  # 120deg * 100

led = Pin('GP25', mode=Pin.OUT)
led(0)  # turn off the heartbeat LED

servo = Servo(servo_pin,
              FREQUENCY,
              ROTATIONAL_RANGE_100,
              PULSE_MIN,
              PULSE_MAX)

servo.angle(desired_angle * 100)
```