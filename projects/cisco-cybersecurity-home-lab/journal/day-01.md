# Day 1 of 15 — Console Access and Baseline Checks ✅

## Goal
Make contact with the Cisco 1921 router and Catalyst 3750G switch through their console ports, identify the hardware and IOS, and document baseline interface state without changing the configuration.

## Lab equipment
- Cisco 1921 integrated services router
- Cisco Catalyst 3750G switch
- MacBook Air using the Terminal application
- USB-to-RJ45 Cisco console cable

## Steps completed
1. Connected the USB end of the console cable to the MacBook.
2. Connected the RJ-45 end to each device's **CONSOLE** port, one device at a time.
3. Connected with macOS Terminal using `screen` and a USB serial device at 9600 baud.
4. Reached a Cisco IOS prompt on the router and switch.
5. Ran baseline show commands and took screenshots.
6. Reviewed reported interface state and logging output.
7. Prepared sanitized evidence images for a public technical portfolio.

## Commands used
```text
show version
show inventory
show ip interface brief
show logging
show running-config
```

> These are observation commands. No configuration change is required for this milestone.

## Results

| Check | Observation | Interpretation |
|---|---|---|
| Cisco 1921 console | IOS CLI responds | Serial console path works |
| Cisco 3750G console | IOS CLI responds | Serial console path works |
| Catalyst IOS | 12.2(55)SE11 | Installed switch software identified |
| Switch `Gi2/0/1` / `Gi2/0/2` | up/up | Active Ethernet links at capture time |
| Router `Gi0/1` | up/up | Active Ethernet link at capture time |
| Router `Gi0/0` | down/down | No active link at capture time; reason not yet established |
| Router syslog | Local logging enabled | Router can produce logs; no remote SIEM verified yet |

**Limits:** These checks do not validate every hardware port, switching, routing, DHCP/NAT, security policy, or Internet connectivity.

## What I learned
- The **console port** lets me manage a Cisco device directly; it is not the same as a normal Ethernet port.
- `show version` identifies IOS and hardware details.
- `show ip interface brief` is a quick way to inspect interface health.
- `up/up` indicates an active interface and line protocol; `down/down` does not automatically indicate broken hardware.
- Documenting an existing configuration is safer than making changes immediately.

## Day 1 video-journal talking points
1. Show the two Cisco devices and the console cable.
2. Show the MacBook Terminal connected to the Cisco IOS prompt.
3. Explain the purpose of `show version` and `show ip interface brief`.
4. Explain the difference between a console port and an Ethernet port.
5. Close with the next mission: discovering switch ports, VLANs, and stack information.

## Evidence

- [Cisco 1921 router console photo](../evidence/03-router-console-version.jpg)
- [Equipment, interface states, and router logging observations](../evidence/observations.md)

## Next step
[Day 2 — Switch inspection](day-02-checklist.md)
