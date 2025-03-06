# Build Xen for Raspberry Pi 4

This script builds Xen, a 64-bit linux kernel from the Raspberry Pi tree, and packages a minimal 64-bit Ubuntu 20.04 rootfs for the Raspberry Pi 4.

A recent version of Ubuntu is required to run the build script. An internet connection is required. 8 GB RAM or more is recommended, and 10GB+ free disk space.

Usage:

    $ ./rpixen.sh

Ensure that the script prints the message "=== BUILD SUCCEEDED ===".
When the script is finished, flash to SD card with (for example):

    $ umount /dev/sdX1
    $ umount /dev/sdX2
    $ sudo dd if=rpixen.img of=/dev/sdX bs=8M
    $ sync

Xen will print messages to the UART.
Log in with username `dornerworks` password `dornerworks`.

To install a graphical desktop, expand the rootfs partition, ensure that you have an internet connection, run the command `sudo apt install ubuntu-desktop`, and reboot.


```
root@raspi4:~# xl dmesg
(XEN) Checking for initrd in /chosen
(XEN) RAM: 0000000000000000 - 000000003b3fffff
(XEN) RAM: 0000000040000000 - 000000007fffffff
(XEN)
(XEN) MODULE[0]: 0000000000200000 - 00000000003450c8 Xen
(XEN) MODULE[1]: 000000002eff6200 - 000000002effff17 Device Tree
(XEN) MODULE[2]: 0000000000480000 - 0000000001c00000 Kernel
(XEN)  RESVD[0]: 0000000000000000 - 0000000000001000
(XEN)  RESVD[1]: 000000003ef66540 - 000000003ef66575
(XEN)
(XEN)
(XEN) Command line: console=dtuart dtuart=/soc/serial@7e215040 sync_console dom0_mem=512M bootscrub=0
(XEN) Domain heap initialised
(XEN) Booting using Device Tree
(XEN) Platform: Raspberry Pi 4
(XEN) Looking for dtuart at "/soc/serial@7e215040", options ""
(XEN) Automatic baud rate determination was requested, but a baud rate was not set up
 Xen 4.15.1
(XEN) Xen version 4.15.1 (root@) (aarch64-none-linux-gnu-gcc (GNU Toolchain for the A-profile Architecture 9.2-2019.12 (arm-9.10)) 9.2.1 20191025) debug=y Tue Mar  4 18:42:57 CST 2025
(XEN) Latest ChangeSet: Fri Sep 10 09:03:24 2021 +0200 git:84fa990
(XEN) build-id: 8dc33ce36bb2fcf602fef8e0631fbed15539f6f6
(XEN) Console output is synchronous.
(XEN) Processor: 410fd083: "ARM Limited", variant: 0x0, part 0xd08, rev 0x3
(XEN) 64-bit Execution:
(XEN)   Processor Features: 0000000000002222 0000000000000000
(XEN)     Exception Levels: EL3:64+32 EL2:64+32 EL1:64+32 EL0:64+32
(XEN)     Extensions: FloatingPoint AdvancedSIMD
(XEN)   Debug Features: 0000000010305106 0000000000000000
(XEN)   Auxiliary Features: 0000000000000000 0000000000000000
(XEN)   Memory Model Features: 0000000000001124 0000000000000000
(XEN)   ISA Features:  0000000000010000 0000000000000000
(XEN) 32-bit Execution:
(XEN)   Processor Features: 00000131:00011011
(XEN)     Instruction Sets: AArch32 A32 Thumb Thumb-2 Jazelle
(XEN)     Extensions: GenericTimer Security
(XEN)   Debug Features: 03010066
(XEN)   Auxiliary Features: 00000000
(XEN)   Memory Model Features: 10201105 40000000 01260000 02102211
(XEN)  ISA Features: 02101110 13112111 21232042 01112131 00011142 00010001
(XEN) SMP: Allowing 4 CPUs
(XEN) enabled workaround for: ARM erratum 1319537
(XEN) Generic Timer IRQ: phys=30 hyp=26 virt=27 Freq: 54000 KHz
(XEN) GICv2 initialization:
(XEN)         gic_dist_addr=00000000ff841000
(XEN)         gic_cpu_addr=00000000ff842000
(XEN)         gic_hyp_addr=00000000ff844000
(XEN)         gic_vcpu_addr=00000000ff846000
(XEN)         gic_maintenance_irq=25
(XEN) GICv2: 256 lines, 4 cpus, secure (IID 0200143b).
(XEN) XSM Framework v1.0.0 initialized
(XEN) Initialising XSM SILO mode
(XEN) Using scheduler: SMP Credit Scheduler rev2 (credit2)
(XEN) Initializing Credit2 scheduler
(XEN)  load_precision_shift: 18
(XEN)  load_window_shift: 30
(XEN)  underload_balance_tolerance: 0
(XEN)  overload_balance_tolerance: -3
(XEN)  runqueues arrangement: socket
(XEN)  cap enforcement granularity: 10ms
(XEN) load tracking window length 1073741824 ns
(XEN) Allocated console ring of 32 KiB.
(XEN) CPU0: Guest atomics will try 14 times before pausing the domain
(XEN) Bringing up CPU1
(XEN) CPU1: Guest atomics will try 13 times before pausing the domain
(XEN) CPU 1 booted.
(XEN) Bringing up CPU2
(XEN) CPU2: Guest atomics will try 13 times before pausing the domain
(XEN) CPU 2 booted.
(XEN) Bringing up CPU3
(XEN) CPU3: Guest atomics will try 13 times before pausing the domain
(XEN) CPU 3 booted.
(XEN) Brought up 4 CPUs
(XEN) I/O virtualisation disabled
(XEN) P2M: 44-bit IPA with 44-bit PA and 8-bit VMID
(XEN) P2M: 4 levels with order-0 root, VTCR 0x80043594
(XEN) Scheduling granularity: cpu, 1 CPU per sched-resource
(XEN) Adding cpu 0 to runqueue 0
(XEN)  First cpu on runqueue, activating
(XEN) Adding cpu 1 to runqueue 0
(XEN) Adding cpu 2 to runqueue 0
(XEN) Adding cpu 3 to runqueue 0
(XEN) alternatives: Patching with alt table 00000000002d4390 -> 00000000002d4b94
(XEN) **** No support for ARM_SMCCC_ARCH_WORKAROUND_1. ****
(XEN) **** Please update your firmware.                ****
(XEN) *** LOADING DOMAIN 0 ***
(XEN) Loading d0 kernel from boot module @ 0000000000480000
(XEN) Allocating 1:1 mappings totalling 512MB for dom0:
(XEN) BANK[0] 0x00000010000000-0x00000028000000 (384MB)
(XEN) BANK[1] 0x00000030000000-0x00000038000000 (128MB)
(XEN) Grant table range: 0x00000000200000-0x00000000240000
(XEN) Allocating PPI 16 for event channel interrupt
(XEN) Loading zImage from 0000000000480000 to 0000000010000000-0000000011780000
(XEN) Loading d0 DTB to 0x0000000018000000-0x00000000180094c7
(XEN) Initial low memory virq threshold set at 0x4000 pages.
(XEN) Std. Loglevel: All
(XEN) Guest Loglevel: All
(XEN) ***************************************************
(XEN) WARNING: CONSOLE OUTPUT IS SYNCHRONOUS
(XEN) This option is intended to aid debugging of Xen by ensuring
(XEN) that all output is synchronously delivered on the serial line.
(XEN) However it can introduce SIGNIFICANT latencies and affect
(XEN) timekeeping. It is NOT recommended for production use!
(XEN) ***************************************************
(XEN) 3... 2... 1...
(XEN) *** Serial input to DOM0 (type 'CTRL-a' three times to switch input)
(XEN) Freed 324kB init memory.

root@raspi4:~# xl info
host                   : raspi4
release                : 5.10.110-v8+
version                : #1 SMP PREEMPT Tue Mar 4 18:46:50 CST 2025
machine                : aarch64
nr_cpus                : 4
max_cpu_id             : 3
nr_nodes               : 1
cores_per_socket       : 1
threads_per_core       : 1
cpu_mhz                : 54.000
hw_caps                : 00000000:00000000:00000000:00000000:00000000:00000000:00000000:00000000
virt_caps              : hvm hap
total_memory           : 1972
free_memory            : 1173
sharing_freed_memory   : 0
sharing_used_memory    : 0
outstanding_claims     : 0
free_cpus              : 0
xen_major              : 4
xen_minor              : 15
xen_extra              : .1
xen_version            : 4.15.1
xen_caps               : xen-3.0-aarch64 xen-3.0-armv7l
xen_scheduler          : credit2
xen_pagesize           : 4096
platform_params        : virt_start=0x200000
xen_changeset          : Fri Sep 10 09:03:24 2021 +0200 git:84fa990
xen_commandline        : console=dtuart dtuart=/soc/serial@7e215040 sync_console dom0_mem=512M bootscrub=0
cc_compiler            : aarch64-none-linux-gnu-gcc (GNU Toolchain for the A-profile Arc
cc_compile_by          : root
cc_compile_domain      :
cc_compile_date        : Tue Mar  4 18:42:57 CST 2025
build_id               : 8dc33ce36bb2fcf602fef8e0631fbed15539f6f6
xend_config_format     : 4
```

## Create DomU on Arm64

This is a fairly minimal example of what is required for a
Paravirtualised Linux guest. For a more complete guide see `xl.cfg(5)`

```
# =====================================================================
# Example PVH Linux guest configuration
# =====================================================================
# Guest name
name = "ubuntu-20.04"

# This configures a PVH rather than PV guest
type = "pvh"

# Kernel image to boot
kernel = "/media/Image"

# Ramdisk (optional)
#ramdisk = "/boot/initrd.gz"

# Kernel command line options
extra = "root=/dev/xvda"

# Initial memory allocation (MB)
memory = 256

# Maximum memory (MB)
#maxmem = 512

# Number of VCPUS
vcpus = 2

# Network devices
vif = [ 'bridge=xenbr0' ]

# Disk Devices
disk = [ 'file:/media/domU.img,xvda,rw' ]
```

```
root@raspi4:~# xl list
Name                                        ID   Mem VCPUs      State   Time(s)
Domain-0                                     0   512     4     r-----     550.6
ubuntu-20.04                                 2   256     2     r-----      24.7
```
