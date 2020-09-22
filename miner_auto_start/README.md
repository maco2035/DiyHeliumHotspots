# Running miner as a service in Raspberry Pi OS or Ubuntu
How to guide on running the miner as a service.
To avoid filling up disk space, this service has any logging turned off.


Donations are welcome! 
#joeytank Thanks you!
HNT donations to: 1367etyj5UnthZrK7AK4KJQwXdy9iYASHetCtSD8s6HkRNa8Asg

1. Download lora-pkt-fwd.service file and save it to the `/etc/systemd/system` directory. This service will reset the GPIO pin as well as start the forwarder

2 - Reload the service daemon
`sudo systemctl daemon-reload`

3 - Start the service
`sudo systemctl start lora-pkt-fwd.service`

4 - Set the service to auto start
`sudo systemctl enable lora-pkt-fwd.service`



