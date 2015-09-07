# Hostname

This is an ansible role to configure the hostname and initial `/etc/hosts`
entries on a Debian-style system.

Role Variables
--------------

    hostname_hostname: "{{inventory_hostname}}"

The host's primary FQDN.

    hostname_shortname: "{{hostname_hostname.split('.')[0]}}"

The host's primary shortname, which by default is the local hostname with
no domain parts.

    hostname_ipaddress: "{{ansible_default_ipv4.address}}"

The host's primary IP address.

    hostname_aliases: []

A list of any other hostname aliases you may want to assign this host.

    hostname_othernames: []

A dict for setting up additional `/etc/hosts` entries. Each entry in the
dict has an `address` element for the IP address and a `hostnames`
element, which can be either a single string or a list of strings,
representing one or more hostnames you want associated with that IP.

Example Playbook
----------------

    - hosts: servers
      roles:
         - slaarti.hostname
      vars:
         hostname_aliases:
           - "testhost"
         hostname_othernames:
           - ipaddress: "127.1.1.1"
             hostnames:
               - "foo"
               - "bar"
           - ipaddress: "127.1.1.2"
             hostnames: "baz"

License
-------

Unlicense; see the LICENSE file for details.

Author Information
------------------

Chris Pinard <slaarti@gmail.com>
