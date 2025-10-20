# Analyse the Torrent
so first i opened the packet using the wireshark and looket for the filter of bt-dht because that the protocol over which packets are transferred after that we chek the link description for a place with the zoo.com written we apply filter and make that as the coloumn and then we look through that for info hash after that we look at that and find the id for that and we put it on the net and find the torrent with io we remove the later part and the part till the io construct a flag and apply that.
e2467cbf021192c241367b892230dc1e05c0580e.

## Flag
picoCTF{ubuntu-19.10-desktop-amd64.iso}

## Solve

- so for this chllenge first i had to read about the protocols over which the torrent passes and found that bt-dht protocol over which the packet passes and then we can apply filter on wire shark and find which all packets are being send in the particular torrent. 
- we look at each of the link and see zoo.com where it comes and we see that and we make it and then we apply filter and we make that as the column according to whih we find the torrent that we need to analyze. 
- we look through the info hash and get the id and put it on the net and get the unbuntu link for it and remove the later part and contruct the flag

## Reference 
None



