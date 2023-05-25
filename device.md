<!--
 FileName:      device
 Author:        8ucchiman
 CreatedDate:   2023-05-25 16:04:17
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     https://vectory.work/flops/
 Description:   ---
-->



# Device

$\frac{inferences}{second} = \frac{operations}{second}\times\frac{1\frac{operations}{inference}}$

- $\frac{operations}{secnod}$.. DNN hardware, DNN model
- $\frac{1\frac{operations}{inference}}$.. DNN model




# FLOP

a single MAC operation

$\frac{operations}{second} = (\frac{1}{\frac{cycles}{operation}}\times\frac{cycles}{second})\times number of PEs \times utilization of PEs$

- $\frac{1}{\frac{cycles}{operation}}\times\frac{cycles}{second}$は単一PEの性能



