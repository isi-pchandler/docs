# Using the Serial Console

## Determining which nodes to connect to

You can determine the nodes allocated to your experiment by looking at the **Reserved Nodes** table on the *Show Experiment* page on the web interface.  DETERLab nodes are generally named 'pcXXX' for nodes at <a href="/ISIUCB/">ISI</a> and 'bpcXXX' for node at <a href="/ISIUCB/">UCB</a>.

## Connecting to the Serial Console

Every node on the testbed has serial console access enabled.  

To connect to a node's serial console, you must first log into `users.deterlab.net` and use the **console** command located in `/usr/testbed/bin` (which should be in every user's PATH by default).  

To connect to a particular node, type `console pcXXX` where *pcXXX* is a node allocated to your experiment.

To disconnect from the console session, type `Ctrl` and then `exit`.  The console command is actually a wrapper for telnet.

## Serial Console Logs

All console output from each node is saved in `/var/log/tiplogs/pcXXX.run`, where *pcXXX* is a node allocated to your experiment.  

This run file is created when nodes are first allocated to an experiment, and the Unix permissions of the run files permit only members of the project to view them.  

!!! warning
    When the experiment is swapped out, the run logs are removed.  In order to preserve them, you must make a copy before swapping out your experiment.

Console logs may be viewed through the web interface on the *Show Experiment* page by clicking on the icon in the Console column of the *Reserved Nodes* table.

## Additional information

* <a href="/core/dell-serial-console/">Dell Serial Console Information</a>