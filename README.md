# Dead Simple Download Proxy

*This project is no longer active as it has been superceded by cims-sidecar.*

An extremely simple tool for speeding up downloads of xml content from
cims-server. It was developed to help the Bioko field team, with slower and
unreliable network connections, synchronize the rather large database content
locally.

# How it works

A member of the field team runs the proxy when the team needs to synchronize the
databases to the tablets. When the proxy starts, it downloads the content once
from the remote openhds server and starts serving the content itself. Members of
the field team can then configure their tablets to point at the proxy and
synchronize using it rather than the remote server

# What is required to run it?

A linux host with the following should be able to run the proxy:

  * Bash
  * Wget
  * Python 2.x
  * Network access to the remote server
  * Network access shared with local tablets

Note that because the proxy downloads its content only once, the network
connections for the remote server and the tablets is not required
simultaneously.

# How do I run it?

Once you have downloaded the source, you just need to find the run-all script
and execute it, either by clicking it (if you're using the graphical
environment) or by typing the run-all command directly on the command line.

# How do I configure the tablets to synchronize to it?

Once the proxy starts, it displays the TCP port number it listens on to the
console, by default 8082. To configure the tablet do the following, in the
*exact* order:

  * Start the cims-tablet application (optional if you're already running it)
  * Login as a supervisor (with the remote server configured)
  * On the sync screen, reconfigure the server to be http://&lt;proxy&gt;:8082/openhds
  * Hit the Sync All button

Note that &lt;proxy&gt; should be the hostname or IP address of the computer running
the proxy.

# Potential Issues

In order for the proxy to work, the host computer's firewall needs to allow
connections on the port it starts on (by default 8082).

