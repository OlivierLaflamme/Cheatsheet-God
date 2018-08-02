loslevel:
--------

Reports back on installed service pack, maintenance etc. levels of the AIX deployment.
Most of these appear to return absolutely nothing or loads of information.

oslevel          (reports back the overall AIX version e.g. 6.1.0.0)
oslevel -q     (reports back known maintenance levels on the host)
oslevel -rq    (reports back known Recommended Maintenance Levels, think major releases)
oslevel -sq    (reports back known Service Packs - has returned a load of service pack numbers for me, these are useful when looking at products in relation to the service pack)

e.g.
oslevel -s -g 6100-08-03-1339

lslpp:
------

Displays information about installed filesets/software and updates. It's particularly useful when coupled with the information returned by itself

e.g.
lslpp -l         (lists all packages, most recent level and state of them)
The package names can be passed back to it for more info, showing their patch management/application cycle.

e.g. 
lslpp -h bos.rte   - returns information regarding the updates applied to the Base Operating System package. bos.rte

rpm:
----

Standard redhat package manager, has turned up on a few machines.

rpm -qa 
rpm -qa --last
These will report back packages installed by rpm and when.

Other than those, it's the same combination of looking through directories and permissions on files. I usually end up checking through with "find" and the "-perm" flag:
e.g. find /home/ -perm 777
