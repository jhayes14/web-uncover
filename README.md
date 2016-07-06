# web-uncover
Decrypt wlan traffic via eapol

###### Disclaimer
This is a tale of how to practically eavesdrop on unencrypted connections on a WLAN. I do not endorse using this for evil. This is supposed to be solely educational.

###### Network Card

Firstly, it is necessary to switch the computers (the on that will be eavesdropping on communications) network card to promiscous mode. By default, network traffic not destined to your computer is not accessible. To passively collect all network traffic in a WLAN, you can change a NIC to promiscous mode. Note there is a subtle difference between monitor and promiscuous mode, explained [here](https://security.stackexchange.com/questions/36997/what-is-the-difference-between-promiscuous-and-monitor-mode-in-wireless-networks). For the purposes of this tutorial you need to be connected to an AP. In ubuntu, you enter promiscuous mode by running ```ifconfig eth1 promisc``` from a terminal.

###### EAPOL

To decrypt a session you need to capture the initial EAPOL handshake.
