From the Red Pitaya Buildroot U-Boot prompt:
```
dcache off                                                                
fatload mmc 0 0x0 blink.bin                                          
dcache flush                                                              
go 0x0    
```
