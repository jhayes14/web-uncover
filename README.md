# web-uncover

The goal of this tutorial is to learn the specific webpages another client is viewing while connected to the same AP as the adversary (you). This then only works for sites served over unencrypted HTTP.

###### Disclaimer
This is a tale of how to practically eavesdrop on WEP/WPA2 traffic. I do not endorse using this for evil. This is supposed to be solely educational.

###### Network Card

Firstly, it is necessary to switch the computers (the on that will be eavesdropping on communications) network card to promiscous mode. By default, network traffic not destined to your computer is not accessible. To passively collect all network traffic in a WLAN, you can change a NIC to promiscous mode. Note there is a subtle difference between monitor and promiscuous mode, explained [here](https://security.stackexchange.com/questions/36997/what-is-the-difference-between-promiscuous-and-monitor-mode-in-wireless-networks). For the purposes of this tutorial you need to be connected to an AP. In ubuntu, you enter promiscuous mode by running ```ifconfig eth1 promisc``` from a terminal.

###### EAPOL

To decrypt a session you need to capture the initial EAPOL handshake. You can read a good summary of the Extensible Authentication Protocol [here](https://sites.google.com/site/amitsciscozone/home/switching/802-1x).
