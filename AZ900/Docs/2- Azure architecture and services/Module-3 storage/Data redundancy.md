
| Redundancy configuration | Deployment                                                                           | Durability |
| ------------------------ | ------------------------------------------------------------------------------------ | ---------- |
| LRS                      | Single Datacenter in the primary region                                              | 11 nines   |
| ZRS                      | Three Availability zones in the primary region                                       | 12 nines   |
| GRS                      | Single datacenter in primary and secondary regions                                   | 16 nines   |
| GZRS                     | 3 availability zones in the primary region and single datacenter in secondary region | 16 nines   | 

^806ad9

![[Pasted image 20231103132442.png | 700]] ^6612e7

why do we need a read only access after any kind of crash **read only GRS**.