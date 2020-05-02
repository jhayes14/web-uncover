# web-uncover

A very quick guide to sniffing and decrypting 802.11 data packets. The goal of this tutorial is to learn the specific webpages another client is viewing while connected to the same AP as the adversary (you). This then only works for sites served over unencrypted HTTP.

###### Disclaimer
This is a tale of how to practically eavesdrop on WEP/WPA2 traffic. I do not endorse using this for evil. This is supposed to be solely educational.

###### Network Card

Firstly, it is necessary to switch the computers (the one that will be eavesdropping on communications) network card to promiscous mode. By default, network traffic not destined to your computer is not accessible. To passively collect all network traffic in a WLAN, you can change a NIC to promiscous mode. Note there is a subtle difference between monitor and promiscuous mode, explained [here](https://security.stackexchange.com/questions/36997/what-is-the-difference-between-promiscuous-and-monitor-mode-in-wireless-networks). For the purposes of this tutorial you need to be connected to an AP. In ubuntu, you enter promiscuous mode by running ```ifconfig eth1 promisc``` from a terminal.

###### EAPOL

To decrypt a session you need to capture the initial EAPOL handshake. You can read a good summary of the Extensible Authentication Protocol [here](https://sites.google.com/site/amitsciscozone/home/switching/802-1x).

###### Capture Traffic

To do this I recommend something like ```tcpdump```. Note on macOS the network card can be directly manipulated by add the ```-I``` flag, though this puts it in monitor mode.

All you need is to specify the device such as ```eth1``` and write to a pcap file ```-w capture.pcap```. We must save as pcap as tcpdump cannot decrypt 802.11 data packets on the fly. This must be done later.

###### Wireshark

Load the saved pcap file. If you started capturing before the target device joined the AP you should see EAPOL packets captured. Supply both the AP name and passphrase to Wireshark and it will then be able to decrypt the captured 802.11 data packets. After decryption, HTTP headers from the target machines session should now be visible.


