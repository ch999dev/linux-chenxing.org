# CIS

https://github.com/wireless-tag-com/openwrt-ssd20x/blob/87d0cbd51907d3f053230381d9277e29ab0194bb/18.06/package/sigmastar/uboot-sstar/src/drivers/mstar/spinand/inc/common/drvSPINAND.h#L67

|      | 0x0                | 0x1                | 0x2               | 0x3               | 0x4                | 0x5                | 0x6           | 0x7           | 0x8                 | 0x9                 | 0xa         | 0xb         | 0xc        | 0xd          | 0xe        | 0xf      | Notes                                                                                                             |
|------|--------------------|--------------------|-------------------|-------------------|--------------------|--------------------|---------------|---------------|---------------------|---------------------|-------------|-------------|------------|--------------|------------|----------|-------------------------------------------------------------------------------------------------------------------|
| 0x0  | 0x4d (M)           | 0x53 (S)           | 0x54 (T)          | 0x41 (A)          | 0x52 (R)           | 0x53 (S)           | 0x45 (E)      | 0x4D (M)      | 0x49 (I)            | 0x55 (U)            |  0x53 (S)   |  0x46 (F)   | 0x44 (D)   | 0x43 (C)     | 0x49 (I)   | 0x53 (S) | Fixed magic header - MSTARSEMIUSFDCIS                                                                             |
| 0x10 | id byte count      | id byte 0          | id byte 1         | id byte 2         | id byte 3          | id byte 4          | id byte 5     | id byte 6     | id byte 7           | id byte 8           | id byte 9   | id byte 10  | id byte 11 | id byte 12   | id byte 13 | id byte  | Seems to be for the ID from the SPI NAND, Might not actually get checked, "GCIS.bin" has 0x2, 0xc2, 0x12, 0x00 .. |
| 0x20 | spare byte count l | spare byte count h | page byte count l | page byte count h | block page count l | block page count h | block count l | block count h | sector byte count l | sector byte count h | plane count | wrap config | RIU read   | clock config | uboot pba  | bl0 pba  | clock config is the max frequency in mhz                                                                          |
| 0x30 | bl1 pba            | hash pba           | hash pba          | hash pba          | hash pba           | hash pba           | hash pba      | read mode     | write mode          |                     |             |             |            |              |            |          |                                                                                                                   |

## Pioneer3

- Most fields don't matter to the boot rom
  - The header is checked
  - The page size is read
  - The sectore size is read
- bl0 defaults to 0xa if it is zero, for 128K blocks this gives an offset of 0x140000
- bl1 defaults to 0xd if it is zero, for 128K blocks this gives an offset of 0x1A0000 (Assuming bl1 is the second copy of the IPL)
