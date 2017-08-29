# opennebula-phpiam
Open Nebula PHPIpam integration

https://docs.opennebula.org/5.4/integration/infrastructure_integration/devel-ipam.html


IPAM Usage
To use your new IPAM module you need to:

Place the four previous scripts in /var/lib/one/remotes/ipam/<ipam_mad>.
Activate the driver in oned.conf by adding the IPAM driver name (same as the one used to name the directory where the action scripts are stored) to the -i option of the IPAM_MAD attribure:
IPAM_MAD = [
    EXECUTABLE = "one_ipam",
    ARGUMENTS  = "-t 1 -i dummy, <ipam_mad>"
]
You need to restart OpenNebula to load the new ipam module.
Now, define Virtual Networks to use the IPAM. Add IPAM_MAD to the AR defintion, for example:
NAME = "IPAM Network"

BRIDGE  = "br0"
VNM_MAD = "dummy"

AR = [
  SIZE     = 21,
  IPAM_MAD = <ipam_mad>
 ]
Any VM (or VNET reservation) from IPAM Network will contanct the IPAM using your drivers.