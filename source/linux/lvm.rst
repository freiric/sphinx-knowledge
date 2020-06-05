LVM Architecture and Terminology

Before we dive into the actual LVM administrative commands, it is important to have a basic understanding of how LVM organizes storage devices and some of the terminology it employs.
LVM Storage Management Structures

LVM functions by layering abstractions on top of physical storage devices. The basic layers that LVM uses, starting with the most primitive, are.

    Physical Volumes:
    
        LVM utility prefix: pv...
        Description: Physical block devices or other disk-like devices (for example, other devices created by device mapper, like RAID arrays) are used by LVM as the raw building material for higher levels of abstraction. Physical volumes are regular storage devices. LVM writes a header to the device to allocate it for management.

    Volume Groups:
    
        LVM utility prefix: vg...
        Description: LVM combines physical volumes into storage pools known as volume groups. Volume groups abstract the characteristics of the underlying devices and function as a unified logical device with combined storage capacity of the component physical volumes.
	
    Logical Volumes:
    
        LVM utility prefix: lv... (generic LVM utilities might begin with lvm...)
        Description: A volume group can be sliced up into any number of logical volumes. Logical volumes are functionally equivalent to partitions on a physical disk, but with much more flexibility. Logical volumes are the primary component that users and applications will interact with.

In summary, LVM can be used to combine physical volumes into volume groups to unify the storage space available on a system. Afterwards, administrators can segment the volume group into arbitrary logical volumes, which act as flexible partitions.


.. code-block::

   pvs
   gvs
   lvs
