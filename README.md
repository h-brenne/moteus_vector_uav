# Sinusoidal Thrust Vectoring Mode for Moteus Driver #
Custom firmware to allow sinusoidal modulation for thrust vectored UAV. Forked from [mjbots/moteus](https://github.com/mjbots/moteus).

Sinusoidal control mode allows command of motor velocity as a sinusoidal signal of the motor position with a DC component.
This can be exploited for thrust vector control of a special type of rotor. The sinusoidal modulation
has been implemented in the motor driver as it needs to happen at a very high rate. 

Sinusoidal mode can be enabled by setting `mode = 16`. Then, PositionCommands can be sent with additional commands
sinusoidal_amplitude and sinusoidal_phase. The velocity setpoint is then given as the `command_velocity*(1+sinusoidal_amplitude_sin(rotor_position+sinusoidal_phase))`

Alternatively to having a sinusoidal velocity setpoint, a sinusoidal torque feedforward can be used. To enable sinsoidal torque feadforward,
set the parameter `servo.sinusoidal_torque_ff = true`. 
The feedforward torque equals `sinusoidal_amplitude*sinusoidal_torque_ff_scale`. `sinusoidal_amplitude` can be a maximum of 1. 

See [original moteus driver](https://github.com/mjbots/moteus) repo for additional information.
# License #

All files contained in this repository, unless otherwise noted, are
available under an Apache 2.0 License:
https://www.apache.org/licenses/LICENSE-2.0
