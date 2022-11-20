# ipsblock
ips to block with ipset in router

Many sources of ips to use in a ipset setup in a router. I use in forward mode to protect network, not just input chain.

ads|spyware|badpeers|spider|webexploit|malicious code|attack|ap2p|spam|flood|virus|kad|p2p|privacy|spy & gov|nso|pegasus

Enjoy.

Use /etc/allowcidr.txt to whitelist a ip/group ip

==================================
firewall.@ipset[0]=ipset
firewall.@ipset[0].name='allowcidr'
firewall.@ipset[0].match='dst_net'
firewall.@ipset[0].storage='hash'
firewall.@ipset[0].maxelem='70000'
firewall.@ipset[0].loadfile='/etc/allowcidr.txt'
firewall.@ipset[0].enabled='1'
firewall.@ipset[0].hashsize='32768'
firewall.@rule[10]=rule
firewall.@rule[10].name='allowcidr'
firewall.@rule[10].family='ipv4'
firewall.@rule[10].ipset='allowcidr'
firewall.@rule[10].target='ACCEPT'
firewall.@rule[10].proto='all'
firewall.@rule[10].src='*'
firewall.@rule[10].dest='*'
firewall.@ipset[1]=ipset
firewall.@ipset[1].name='dropcidr'
firewall.@ipset[1].storage='hash'
firewall.@ipset[1].match='dst_net'
firewall.@ipset[1].maxelem='700000'
firewall.@ipset[1].loadfile='/etc/dropcidr.txt'
firewall.@ipset[1].enabled='1'
firewall.@ipset[1].hashsize='32768'
firewall.@rule[11]=rule
firewall.@rule[11].name='dropcidr'
firewall.@rule[11].ipset='dropcidr'
firewall.@rule[11].target='REJECT'
firewall.@rule[11].src='*'
firewall.@rule[11].dest='*'
firewall.@rule[11].family='ipv4'
firewall.@rule[11].extra='-j REJECT --reject-with icmp-net-unreachable'
firewall.@rule[11].proto='all'
==================================

