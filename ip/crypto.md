[rough register descriptions](https://github.com/fifteenhex/linux-ssc325/blob/v4.9.84-sigmastar/drivers/sstar/crypto/hal/infinity3/halAESDMA.h)

https://github.com/linux-chenxing/linux-ssc325/blob/takoyaki_dls00v050/drivers/sstar/crypto/halAESDMA.c

### RNG

RNG block registermap:

| Offset | Name   | 15 | 14 | 13 | 12 | 11 | 10 | 9 | 8 | 7       | 6 | 5 | 4 | 3 | 2 | 1            | 0      | Comment                                     |
|--------|--------|----|----|----|----|----|----|---|---|---------|---|---|---|---|---|--------------|--------|---------------------------------------------|
| 0x00   | CTRL   |    |    |    |    |    |    |   |   | enable? | ? | ? | ? | ? | ? | 1 by default | ?      |                                             |
| 0x04   | ???    |    |    |    |    |    |    |   |   |         |   |   |   |   |   |              |        | Reads 0x30, can write 0xffff                |
| 0x08   | VALUE  |    |    |    |    |    |    |   |   |         |   |   |   |   |   |              |        | The output value. Ready when STATUS[0] is 1 |
| 0x0C   | STATUS |    |    |    |    |    |    |   |   |         |   |   |   |   |   |              | ready? |                                             |

### SHA

This is a hardware SHA1/SHA256 unit.

Clock is comes from the same mux as "aesdma"

SHA block registermap:

| Offset    | Name       | 15 | 14          | 13             | 12 | 11                      | 10 | 9         | 8 | 7    | 6        | 5    | 4 | 3 | 2    | 1              | 0              | Comment                                                                          |
|-----------|------------|----|-------------|----------------|----|-------------------------|----|-----------|---|------|----------|------|---|---|------|----------------|----------------|----------------------------------------------------------------------------------|
| 0x20      | CTRL       |    | CTRL_MANUAL | CTRL_INIT_HASH |    | DISABLE SCATTER GATHER? |    | CTRL_MODE | ? |      | CTRL_CLR |      |   |   |      |                | CTRL_FIRE_ONCE | write 1 to fire once,  0 = SHA-1  1 = SHA-256  enable/disable initial hash value |
| 0x28      | SRC_L      |    |             |                |    |                         |    |           |   |      |          |      |   |   |      |                |                |                                                                                  |
| 0x2C      | SRC_H      |    |             |                |    |                         |    |           |   |      |          |      |   |   |      |                |                |                                                                                  |
| 0x30      | LEN_L      |    |             |                |    |                         |    |           |   |      |          |      |   |   |      |                |                |                                                                                  |
| 0x34      | LEN_H      |    |             |                |    |                         |    |           |   |      |          |      |   |   |      |                |                |                                                                                  |
| 0x38      | MIUSEL     |    |             |                |    |                         |    |           |   | MIU0 |          | MIU1 |   |   |      |                |                |                                                                                  |
| 0x3C      | STATUS     |    |             |                |    |                         |    |           |   |      |          |      |   |   |      | BUSY           |  READY         |                                                                                  |
| 0x40-0x5f | VALUE      |    |             |                |    |                         |    |           |   |      |          |      |   |   |      |                |                | When reading - the output value, when writing - initial hash value (big endian)  |
| 0xB8      | WORD_CNT_L |    |             |                |    |                         |    |           |   |      |          |      |   |   |      |                |                | count in 4-byte words, lower 16 bits                                             |
| 0xBC      | WORD_CNT_H |    |             |                |    |                         |    |           |   |      |          |      |   |   |      |                |                | higher 16 bits                                                                   |

### RSA

| Offset | Name       | 15  | 14  | 13  | 12  | 11  | 10  | 9   | 8   | 7 | 6 | 5 | 4 | 3                 | 2              | 1          | 0           |    | Comment |
|--------|------------|-----|-----|-----|-----|-----|-----|-----|-----|---|---|---|---|-------------------|----------------|------------|-------------|----|---------|
| 0x80   |            |     |     |     |     |     |     |     |     |   |   |   |   |                   |                |            | IND32_START |    |         |
| 0x84   | IND32      |     |     |     |     |     |     |     |     |   |   |   |   | ACCESS_AUTO_START | ADDR_AUTO_INC  | WRITE      |             |    |         |
| 0x88   | ADDR       |     |     |     |     |     |     |     |     |   |   |   |   |                   |                |            |             |    |         |
| 0x8c   | DATA_L     |     |     |     |     |     |     |     |     |   |   |   |   |                   |                |            |             |    |         |
| 0x90   | DATA_H     |     |     |     |     |     |     |     |     |   |   |   |   |                   |                |            |             |    |         |
| 0x94   | FILE OUT?  |     |     |     |     |     |     |     |     |   |   |   |   |                   |                |            |             |    |         |
| 0x98   | FILE OUT?  |     |     |     |     |     |     |     |     |   |   |   |   |                   |                |            |             |    |         |
| 0x9c   |            |     |     |     |     |     |     |     |     |   |   |   |   |                   |                | INT_CLR    | EXP_START   |    |         |
| 0xa0   | KEY_CONFIG | LEN | LEN | LEN | LEN | LEN | LEN | LEN | LEN |   |   |   |   |                   | SEL_PUBLIC_KEY | SEL_HW_KEY | RST         |    |         |
| 0xa4   | STATUS     |     |     |     |     |     |     |     |     |   |   |   |   | ?                 | ?              | DONE       | BUSY        | RO |         |

ADDR seems to be a pointer to internal sram that is loaded indirectly via data_l and data_h

IND32_START - seems to trigger indirect loading.

E - 0x00
N - 0x40
A - 0x80
Z - 0xC0

LEN - Apparently defaults to 0x3f if the hardware key is selected.

### AESDMA

For infinity2m and infinity6 seem to support 256 bit keys. Everything else seems to only support 128 bit keys.

| Offset | Name        | 15 | 14 | 13        | 12        | 11      | 10 | 9       | 8       | 7      | 6          | 5       | 4 | 3       | 2      | 1 | 0        | Comment          |
|--------|-------------|----|----|-----------|-----------|---------|----|---------|---------|--------|------------|---------|---|---------|--------|---|----------|------------------|
| 0x140  | CTRL0       |    |    |           |           |         |    |         | FOUT_EN | RESET  |            |         |   |         |        |   | FILE_ST  | Can write 0xffff |
| 0x144  | CTRL1       |    |    | CHAINMODE | CHAINMODE |         |    | DECRYPT | AES_EN  |        |            |         |   | TDES_EN | DES_EN |   |          | Can write 0xffff |
| 0x148  | SRC L       |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x14c  | SRC H       |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x150  | XIU LEN L   |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x154  | XIU LEN H   |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x158  | DST START L |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x15c  | DST START H |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x160  | DST END L   |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x164  | DST END H   |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x178  | INTERRUPT   |    |    |           |           |         |    |         |         | INT_EN |            |         |   |         |        |   |          |         |
| 0x19c  | KEY         |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1a0  | KEY         |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1a4  | KEY         |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1a8  | KEY         |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1ac  | KEY         |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1b0  | KEY         |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1b4  | KEY         |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1b8  | KEY         |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1bc  | IV          |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1c0  | IV          |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1c4  | IV          |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1c8  | IV          |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1cc  | IV          |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1d0  | IV          |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1d4  | IV          |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1d8  | IV          |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1dc  | ENG3_CTRL_S |    |    | KEYLEN    | KEYLEN    | KEYBANK |    |         |         |        |            |         |   |         |        |   |          |         |
| 0x1e4  | KEY CONFIG  |    |    |           |           |         |    |         |         |        | KEY_SEL    | KEY_SEL |   |         |        |   |          |         |
| 0x1fc  | STATUS      |    |    |           |           |         |    |         |         |        |            |         |   |         |        |   | DMA_DONE |         |

CHAINMODE:
  - 0b00 - ECB
  - 0b01 - CTR
  - 0b10 - CBC

KEY_SEL:
  - 0b00 - Cipher Key
  - 0b01 - EFUSE key
  - 0b10 - HW key
  
KEYLEN:
  Probably i2m and i6 only
  - 0b00 - 128
  - 0b01 - 192
  - 0b10 - 256
  
KEYBANK:
  For >128 bit keys this selects the second bank/page of the key

```
1f224540: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f224550: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f224560: ffff 0000 ffff 0000 0000 0000 0000 0000    ................
1f224570: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f224580: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f224590: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f2245a0: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f2245b0: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f2245c0: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f2245d0: 0000 0000 0000 0000 0000 0000 0000 0000    ................
1f2245e0: aeda 0000 0000 0000 0000 0000 0000 0000    ................
1f2245f0: 0000 0000 0000 0000 0000 0000 0101 0000    ................
```


On infinity3 the base address is 0x1f224400
