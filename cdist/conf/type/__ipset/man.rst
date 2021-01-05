cdist-type__ipset(7)
====================

NAME
----
cdist-type__ipset - Manage ipset sets

DESCRIPTION
-----------
Making use of ipset sets in iptable rules can make your rules more expressive, maintainable and efficient.

REQUIRED PARAMETERS
-------------------
type
    One of the supported ipset set types, for a full list see:

        ``ipset help``

OPTIONAL PARAMETERS
-------------------
add
    The entry that must exist in the given set.

    Can be used multiple times.
del
    The entry that must not exist in the given set.

    Can be used multiple times.
state
    Can be:

    - ``present``: ensure that the given set exists.
    - ``absent``: ensure the given set doesn't exist.

BOOLEAN PARAMETERS
------------------
None.

EXAMPLES
--------

.. code-block:: sh

    # Make sure a set with the given name/type exists:
    __ipset testset1 --type hash:ip

    # Ensure allowed_ssh_clients contains private range:
    __ipset allowed_ssh_hosts --type hash:net \
        --add 192.168.0.0/24 --add 10.0.0.0/8

    # Make sure host is not on the blocked list:
    __ipset blocked_hosts --type hash:ip \
        --del 1.2.3.4


SEE ALSO
--------
:strong:`cdist-type__iptables_rule`\ (7), :strong:`iptables`\ (8)

AUTHORS
-------
Mesar Hameed <mesar.hameed--@--gmail.com>

COPYING
-------
Copyright \(C) 2021 Mesar Hameed. You can redistribute it
and/or modify it under the terms of the GNU General Public License as
published by the Free Software Foundation, either version 3 of the
License, or (at your option) any later version.
