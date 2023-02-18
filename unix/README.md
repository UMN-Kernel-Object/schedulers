# Booting UNIX v6 Using SimH

## File Tree

```
.
├── README		# You are here
├── boot.ini		# SimH instructions to boot
├── dist.tap		# Unix v6 Distribution Tape
├── printer.txt		# Printer
├── rk			# Storage "Disks"
│   ├── rk0
│   ├── rk1
│   └── rk2
└── sys			# Kernel source
    └── ken		# Ken Thompson's Work (presumably)
        └── slp.c	# Scheduler routines (what we care about)
```

## Prerequisites

This guide expects that you have a recent version of SimH installed on your
system. You can install SimH binaries using your system's package manager or
download them from the SimH
[releases](https://github.com/simh/simh/releases/tag/v3.9-0). Alternatively,
you can build SimH using the instructions
[here](https://github.com/simh/simh#building-simulators-yourself).

## Instructions

This repo should include a pre-setup UNIX v6 image for you to use with SimH.

Open a shell and run:
```
simh-pdp11 boot.ini
```

This will place you in the bootloader. Type "unix" to boot Unix v6.

Your screen should look something like this:

```
PDP-11 simulator V4.0-0 Current
Disabling XQ
boot.ini-5> attach rk0 rk/rk0
%SIM-ERROR: RK device: Non-existent parameter - RK05 # these errors are okay
boot.ini-6> attach rk1 rk/rk1
%SIM-ERROR: RK device: Non-existent parameter - RK05
boot.ini-7> attach rk2 rk/rk2
%SIM-ERROR: RK device: Non-existent parameter - RK05
boot.ini-12> att dci 5555
%SIM-INFO: Listening on port 5555
@unix

login:
```

The login is `root`. There is no default password.

That is it. You are in the system.

Unix v6 didn't have cd. Instead use `chdir` to change directories.

## Links

[SimH Users' Guide](http://simh.trailing-edge.com/pdf/simh_doc.pdf)
[UNIX v6 Tape](https://www.tuhs.org/Archive/Distributions/Other/OS_Course/v6/)
[UNIX v6 SimH Installation Guide](https://gunkies.org/wiki/Installing_UNIX_v6_(PDP-11)_on_SIMH)
