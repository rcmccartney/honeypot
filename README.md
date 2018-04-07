# Honeypot Assignment

### Honeypots deployed

The following shows the 4 types of of honeypots deployed and the number of attacks encountered for each:

![](sensors.png)

More information on each:
*  [Dionaea](https://github.com/threatstream/mhn/wiki/Dionaea-Sensor)
*  [Wordpot](https://github.com/threatstream/mhn/wiki/Wordpot-Sensor)
*  [Snort](https://github.com/threatstream/mhn/wiki/Snort-Sensor)
*  [Conpot](https://github.com/threatstream/mhn/wiki/Conpot-Sensor)

### Issues encountered

As you can see from the previous image, the Wordpot sensor received zero attacks.
When scanned with nmap, the following output was seen:

```bash
$ nmap 35.188.20.24 
Starting Nmap 7.70 ( https://nmap.org ) at 2018-04-06 22:35 PDT                                                                        
Nmap scan report for 24.20.188.35.bc.googleusercontent.com (35.188.20.24)                                                              
Host is up (0.088s latency).
Not shown: 992 closed ports
PORT     STATE    SERVICE
22/tcp   open     ssh
135/tcp  filtered msrpc
139/tcp  filtered netbios-ssn
445/tcp  filtered microsoft-ds
1023/tcp filtered netvenuechat
1720/tcp open     h323q931
2967/tcp filtered symantec-av
9898/tcp filtered monkeycom
```

The Wordpot is supposed to detect probes of a Wordpress installation.
But as you can see, port 80 or 443 are not open, which we would expect
to be for an http/https service.  So it is unclear if this is perhaps
the reason that it was never probed.  

### Data collected

The earlier sensor page showed the number of attacks collected per
honeypot over the course of the week. A visualization of this on
the map for a reduced period of time is the following:

![](worldmap.png)

Using the REST API, we can call the following to get the highest
number of attackers: `/api/top_attackers/?api_key=XXXX&hours_ago=72`

We see the most number of attacks (1013) from 99.244.99.220.
Calling `/api/attacker_stats/99.244.99.220/?api_key=XXXX`
we see that they have conducted port scans over most of the honeypot.

The full output of the data collected is located in 
[session.json](https://github.com/rcmccartney/honeypot/blob/master/session.json). 

### Unresolved questions

None

