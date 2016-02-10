PyMuninCli
==========

PyMuninCli is a Python library that can be used to access a running Munin node
daemon. It implements the client-side of the [Munin network protocol][1] that
is otherwise used by Munin master to fetch configuration and measurements from
monitored hosts on the network.

PyMuninCli can be useful if you want to poll data from an existing Munin node
into some other process, independent of Munin master.

[1]: https://munin.readthedocs.org/en/latest/master/network-protocol.html


Usage
-----

    >>> import munin.client
    >>> import pprint
    >>> conn = munin.client.Client(host="localhost")
    >>> conn.connect()
    >>> conn.list()
    ['processes', 'uptime']
    >>> pprint.pprint(conn.config('uptime'))
    {'uptime': {'graph_args': '--base 1000 -l 0',
                'graph_category': 'system',
                'graph_scale': 'no',
                'graph_title': 'Uptime',
                'graph_vlabel': 'uptime in days',
                'uptime': {'draw': 'AREA', 'label': 'uptime'}}}
    >>> pprint.pprint(conn.fetch('uptime'))
    {'uptime': {'uptime': 27.11}}


License
-------

This version of the library is based on [PyMuninCli by Julien Danjo][2] and has
been modified by Tomaz Solc.

Copyright (c) 2012  Julien Danjou <julien@danjou.info>

Copyright (c) 2016  Tomaz Solc <tomaz.solc@tablix.org>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

[2]: https://julien.danjou.info/projects/pymunincli/
