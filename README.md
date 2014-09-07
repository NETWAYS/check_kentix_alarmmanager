check_kentix_alarmmanager
=========================

Checks the status of Kentix devices.

### Requirements

* Python libraries: `pysnmp`, `nagaconda` (shipped)


### Usage

    check_kentix -h HOST [-p PORT] [-t TIMEOUT] [-w WARNING] [-c CRITICAL]

Example:

    ./check_kentix -h <host> \
        -w check_kentix::sensor_0::temp=~:25 \
        -c check_kentix::sensor_0::temp=~:30 \
        -c check_kentix::sensor_0::active=1:

    This check would be CRITICAL if one of the following conditions are met:
    -The check request fails (wrong IP address, device unavailable, etc.).
    -The first sensor's temperature value is above 30.
    -The first sensor is not active.
    
    The check would return a WARNING if the temperature value is above 25 unless
    one of the CRITICAL conditions were encountered - in which case
    the CRITICAL condition takes precedence.


