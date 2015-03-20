03-06-2015
==========

Problems
--------
* Starting openshift-master and openshift-sdn-master without pausing fails
* Lots of i/o timeouts when pulling from Red Hat registry
* Lost private network routes (192.168.100.0/24) on nodes upon initial configuration.  Rebooting fixed the issue.

Questions
---------
* DNS based routing? https://github.com/GoogleCloudPlatform/kubernetes/blob/master/docs/dns.md
* What does the pod container do exactly?
