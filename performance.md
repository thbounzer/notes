## Some notes on collecting performance data from system 

### First 60 seconds triage (from brendan gregg) 

  vmstat 1         (Virtual memory stats, sample every sec)
  mpstat -P ALL 1  (Processor related stats, all avail CPUS, sample every sec)
  pidstat 1        (Linux tasks statustics, sample every sec)
  iostat -xz 1     (Input/Output stats, x display extend. stats, z omit output no active devices, sample every sec) 
  free -m
  sar -n DEV 1      (use sar, network statistics, network devices, sample every second)
  sar -n TCP,ETCP 1 (use sar, network statistics, tcp v4 stats, tcpv4 errs) 
