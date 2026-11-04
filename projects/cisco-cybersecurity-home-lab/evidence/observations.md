# Day 1 evidence — What the console showed

I connected my MacBook Air to a Cisco 1921 router and a Catalyst 3750G switch, one console port at a time. These notes record the fields I could see in the Day 1 photos. They describe the devices at the time of the check.

| Device | What I checked | What I saw |
| --- | --- | --- |
| Cisco 1921 router | Model and interfaces | The [router console photo](03-router-console-version.jpg) shows model `CISCO1921/K9` and two Gigabit Ethernet interfaces. |
| Catalyst 3750G switch | Software version | `show version` reported Cisco IOS `12.2(55)SE11`. |
| Cisco 1921 router | Logging | `show logging` reported that syslog logging was enabled. The console logging line showed 21 messages logged. I did not test delivery to a SIEM on Day 1. |

## Ethernet links

In the output of `show ip interface brief`, the first column below names the device and port; the last two columns record the interface and line protocol status.

| Device and port | Interface | Line protocol |
| --- | --- | --- |
| Router `Gi0/0` | down | down |
| Router `Gi0/1` | up | up |
| Switch `Gi2/0/1` | up | up |
| Switch `Gi2/0/2` | up | up |
| Switch `Gi2/0/3` through `Gi2/0/20` (rows visible in the photo) | down | down |

The port numbers helped me resolve an earlier point of confusion: `Gi0/1` appears on the **router**, while the first physical port shown on my **switch** is `Gi2/0/1`. Checking the switch's own output gave me the right name to use in later configuration work.

The two active switch links are a starting point. I did not test traffic between endpoints or verify every physical port in this session.

[Back to the Day 1 journal](../journal/day-01.md)
