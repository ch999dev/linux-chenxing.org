# infinity2 pinouts

## 128 QFN (SSD201/SSD202D)

[vendor padmux table](https://github.com/linux-chenxing/linux-ssc325/blob/93240ba80ed1eff069eaca968e5b02be0fdaf273/drivers/sstar/gpio/infinity2m/padmux_tables.c)

- Note: This might not be accurate
- Subscript == mux value for function.

| #  | name         | alt functions        | #  | name                                       | alt functions                                                                                | #  | name               | alt functions                                                                                                                           | #   | name                                 | alt functions                             |
|----|--------------|----------------------|----|--------------------------------------------|----------------------------------------------------------------------------------------------|----|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------|-----|--------------------------------------|-------------------------------------------|
| 1  | GPIO12       | pwm3<sup>3</sup>     | 33 | [PM_RESET](/ip/commonpins.md#pm_reset)     |                                                                                              | 65 | TTL6               | mipi_tx_p_ch0<sup>1/2</sup> ttl_dout2<sup>7/10</sup> ttl_dout4<sup>12/13</sup> ttl_dout6<sup>1</sup>                                    | 97  | SD_D2<sup>1</sup>                    |                                           |
| 2  | GPIO13       |                      | 34 | [PM_UART_RX](/ip/commonpins.md#pm_uart_rx) |                                                                                              | 66 | TTL7               | mipi_tx_n_ch0<sup>1/2</sup> ttl_dout5<sup>12/13</sup> ttl_dout7<sup>1</sup> ttl_dout3<sup>7/10</sup>                                    | 98  | VDDP_1                               |                                           |
| 3  | GPIO14       |                      | 35 | [PM_UART_TX](/ip/commonpins.md#pm_uart_tx) |                                                                                              | 67 | TTL8               | mipi_tx_p_ch1<sup>1/2</sup> ttl_dout6<sup>12/13</sup> ttl_dout8<sup>1</sup> ttl_dout4<sup>7/10</sup>                                    | 99  | GPIO0                                | eth1_mdio<sup>5</sup> i2s_wck<sup>3</sup> |
| 4  | VDD          |                      | 36 | GPIO47 (UART0_RX)                          |                                                                                              | 68 | TTL9               | mipi_tx_n_ch1<sup>1/2</sup> ttl_dout7<sup>12/13</sup> ttl_dout9<sup>1</sup> ttl_dout5<sup>7/10</sup>                                    | 100 | GPIO1                                | eth1_mdc<sup>5</sup> i2s_bck<sup>3</sup>  |
| 5  | GPIO85       |                      | 37 | GPIO48 (UART0_TX)                          |                                                                                              | 69 | TTL10              | mipi_tx_p_ch2<sup>1/2</sup> ttl_dout8<sup>12/13</sup> ttl_dout10<sup>1</sup> ttl_dout6<sup>7/10</sup>                                   | 101 | GPIO2                                | i2c1_scl<sup>1</sup> i2s_sdi<sup>3</sup>  |
| 6  | GPIO86       |                      | 38 | [UART1_RX](/ip/commonpins.md#uart1_rx)     |                                                                                              | 70 | TTL11              | mipi_tx_n_ch2<sup>1/2</sup> ttl_dout9<sup>12/13</sup> ttl_dout11<sup>1</sup> ttl_dout7<sup>7/10</sup>                                   | 102 | GPIO3                                | i2c1_sda<sup>1</sup> i2s_sdo<sup>3</sup>  |
| 7  | DMIC_R       | dmic_d1<sup>2</sup>  | 39 | [UART1_TX](/ip/commonpins.md#uart1_tx)     | ttl_de<sup>12/13</sup>                                                                       | 71 | TTL12              | mipi_tx_p_ch3<sup>1</sup> ttl_dout10<sup>12/13</sup> ttl_dout12<sup>1</sup> ttl_dout8<sup>7/10</sup>                                    | 103 | [PM_LED0](/ip/commonpins.md#pm_led0) |                                           |
| 8  | DMIC_L       | dmic_d0<sup>2</sup>  | 40 | VDDIO_DATA                                 |                                                                                              | 72 | TTL13              | mipi_tx_n_ch3<sup>1</sup> ttl_dout11<sup>12/13</sup> ttl_dout13<sup>1</sup> ttl_dout9<sup>7/10</sup>                                    | 104 | [PM_LED1](/ip/commonpins.md#pm_led1) |                                           |
| 9  | DMIC_CLK     | dmic_clk<sup>2</sup> | 41 | AVDDIO_DRAM                                |                                                                                              | 73 | TTL14              | mipi_tx_p_ch4<sup>1</sup> ttl_dout12<sup>12/13</sup> ttl_dout14<sup>1</sup> ttl_dout10<sup>7/10</sup> i2c0_?<sup>3</sup>                | 105 | VDD                                  |                                           |
| 10 | GPIO90       |                      | 42 | VDD                                        |                                                                                              | 74 | TTL15              | mipi_tx_n_ch4<sup>1</sup> ttl_dout13<sup>12/13</sup> ttl_dout15<sup>1</sup> ttl_dout11<sup>7/10</sup> i2c0_?<sup>3</sup>                | 106 | AVDD_ETH                             |                                           |
| 11 | VDDP_0       |                      | 43 | VDDIO_DATA                                 |                                                                                              | 75 | AVDD1              |                                                                                                                                         | 107 | ETH_RN                               |                                           |
| 12 | VDD          |                      | 44 | VDDIO_DATA                                 |                                                                                              | 76 | VDDP_1             |                                                                                                                                         | 108 | ETH_RP                               |                                           |
| 13 | AVDD_XTAL    |                      | 45 | VDDIO_DATA                                 |                                                                                              | 77 | VDD                |                                                                                                                                         | 109 | ETH_TN                               |                                           |
| 14 | XTAL_IN      |                      | 46 | AVDDIO_DRAM                                |                                                                                              | 78 | VDD                |                                                                                                                                         | 110 | ETH_TP                               |                                           |
| 15 | XTAL_OUT     |                      | 47 | AVSSIO_DQ                                  |                                                                                              | 79 | TTL16              | eth1_mdio<sup>3</sup> spi0_cz<sup>2</sup> ttl_dout12<sup>7/10</sup> ttl_dout14<sup>12/13</sup> ttl_dout16<sup>1</sup>                   | 111 | DP_P2                                |                                           |
| 16 | SE_XTAL_OUT  |                      | 48 | AVDD_PLL                                   |                                                                                              | 80 | TTL17              | eth1_mdc<sup>3</sup> spi0_ck<sup>2</sup> ttl_dout13<sup>7/10</sup> ttl_dout15<sup>12/13</sup> ttl_dout17<sup>1</sup>                    | 112 | DM_P2                                |                                           |
| 17 | AVDD_RTC     |                      | 49 | DVDD_DDR                                   |                                                                                              | 81 | TTL18              | eth1_col<sup>3</sup> spi0_di<sup>2</sup> ttl_dout14<sup>7/10</sup> ttl_dout16<sup>12</sup> ttl_dout18<sup>1</sup>                       | 113 | AVDD_USB                             |                                           |
| 18 | XTAL_IN_32K  |                      | 50 | DVDD_DDR_RX                                |                                                                                              | 82 | TTL19              | eth1_rxd0<sup>3</sup> spi0_do<sup>2</sup> ttl_dout15<sup>7/10</sup> ttl_dout17<sup>12</sup> ttl_dout19<sup>1</sup>                      | 114 | AVDD_AUD                             |                                           |
| 19 | XTAL_OUT_32K |                      | 51 | VDD                                        |                                                                                              | 83 | TTL20              | eth1_rxd1<sup>3</sup> ttl_dout16<sup>7</sup> ttl_dout18<sup>12</sup> ttl_dout20<sup>1</sup>                                             | 115 | AUD_LINEOUT_R0                       |                                           |
| 20 | SAR_GPIO2    |                      | 52 | FUART_RX<sup>1/2</sup>                     | ttl_vsync<sup>12/13</sup> ej_clk<sup>1</sup>                                                 | 84 | TTL21              | eth1_tx_clk<sup>3</sup> eth1_txd1<sup>5</sup> ttl_dout17<sup>7</sup> ttl_dout19<sup>12</sup> ttl_dout21<sup>1</sup>                     | 116 | AUD_LINEOUT_L0                       |                                           |
| 21 | SAR_GPIO1    |                      | 53 | FUART_TX<sup>1/2</sup>                     | ttl_hsync<sup>12/13</sup> ej_tms<sup>1</sup>                                                 | 85 | TTL22              | eth1_txd0<sup>3/5</sup> ttl_dout18<sup>7</sup> ttl_dout20<sup>12</sup> ttl_dout22<sup>1</sup> i2c1_sc?<sup>4</sup>                      | 117 | AUD_MICCM0                           |                                           |
| 22 | SAR_GPIO0    |                      | 54 | FUART_CTS<sup>1</sup>                      | ttl_ck<sup>12/13</sup> i2c1_scl<sup>3</sup> ej_tdo<sup>1</sup>                               | 86 | TTL23              | eth1_txd1<sup>3</sup> eth1_tx_en<sup>5</sup> ttl_dout19<sup>7</sup> ttl_dout21<sup>12</sup> ttl_dout23<sup>1</sup> i2c1_sc?<sup>4</sup> | 118 | AUD_MICIN0                           |                                           |
| 23 | AVDD_NODIE   |                      | 55 | FUART_RTS<sup>1</sup>                      | ttl_dout0<sup>12/13</sup> i2c1_sda<sup>3</sup> ej_tdi<sup>1</sup>                            | 87 | TTL24              | eth1_tx_en<sup>3</sup> eth1_tx_clk<sup>5</sup> ttl_dout20<sup>7</sup> ttl_ck<sup>1</sup> ttl_dout22<sup>12</sup>                        | 119 | AUD_VRM_DAC                          |                                           |
| 24 | GND_EFUSE    |                      | 56 | TTL0                                       | ttl_dout0<sup>1</sup> ttl_dout1<sup>12/13</sup> ttl_de<sup>7/10</sup>                        | 88 | TTL25              | eth1_col<sup>5</sup> ttl_hsync<sup>1</sup> ttl_dout21<sup>7</sup> ttl_dout23<sup>12</sup>                                               | 120 | AUD_VAG                              |                                           |
| 25 | VDD          |                      | 57 | TTL1                                       | ttl_dout1<sup>1</sup> ttl_dout2<sup>12/13</sup> ttl_vsync<sup>7/10</sup> i2c0_?<sup>2</sup>  | 89 | TTL26              | eth1_rxd0<sup>5</sup> ttl_vsync<sup>1</sup> ttl_dout22<sup>7</sup>                                                                      | 121 | GPIO4                                | pwm0<sup>3</sup> ej_?<sup>3</sup>         |
| 26 | PM_SPI_CZ    |                      | 58 | TTL2                                       | ttl_dout2<sup>1</sup> tl_dout3<sup>12/13</sup> ttl_hsync<sup>7/10</sup>  i2c0_?<sup>2</sup>  | 90 | TTL27              | eth1_rxd1<sup>5</sup> ttl_de<sup>1</sup> ttl_dout23<sup>7</sup>                                                                         | 122 | GPIO5                                | pwm1<sup>4</sup> ej_?<sup>3</sup>         |
| 27 | PM_SPI_CK    |                      | 59 | TTL3                                       | ttl_dout3<sup>1</sup> ttl_ck<sup>7/10</sup>                                                  | 91 | PM_SD_CDZ          |                                                                                                                                         | 123 | GPIO6                                | i2c0_scl<sup>4</sup> ej_?<sup>3</sup>     |
| 28 | PM_SPI_DI    |                      | 60 | TTL4                                       | ttl_dout4<sup>1</sup> ttl_dout0<sup>7/10</sup>                                               | 92 | SD_D1<sup>1</sup>  | pwm2<sup>6</sup>                                                                                                                        | 124 | GPIO7                                | i2c0_sda<sup>4</sup> ej_?<sup>3</sup>     |
| 29 | PM_SPI_DO    |                      | 61 | TTL5                                       | ttl_dout5<sup>1</sup> ttl_dout1<sup>7/10</sup>                                               | 93 | SD_D0<sup>1</sup>  | i2s_wck<sup>3</sup>                                                                                                                     | 125 | UART2_RX                             | spi0_cz<sup>5</sup>                       |
| 30 | PM_SPI_HLD   |                      | 62 | DP_P1                                      |                                                                                              | 94 | SD_CLK<sup>1</sup> | i2c1_scl<sup>5</sup> i2s_bck<sup>3</sup>                                                                                                | 126 | UART2_TX                             | spi0_ck<sup>5</sup>                       |
| 31 | PM_SPI_WPZ   |                      | 63 | DM_P1                                      |                                                                                              | 95 | SD_CMD<sup>1</sup> | i2c1_sda<sup>5</sup> i2s_sdi<sup>3</sup>                                                                                                | 127 | GPIO10                               | spi0_di<sup>5</sup>                       |
| 32 | PM_IRIN      |                      | 64 | AVDD_USB                                   |                                                                                              | 96 | SD_D3<sup>1</sup>  | i2s_sdo<sup>3</sup>                                                                                                                     | 128 | GPIO11                               | spi0_do<sup>5</sup>                       |

## 128 QFN SSD203D

https://lceda.cn/component/9d7bb03e05594e07adf6cb0825ab3f3e

## 128 QFN SSR261

- TTL7 and TTL8 are the same as SSD202D?

| #  | name       | #  | name | #  | name | #   | name |
|----|------------|----|------|----|------|-----|------|
| 1  |            | 33 |      | 65 |      | 97  |      |
| 2  |            | 34 |      | 66 |      | 98  |      |
| 3  |            | 35 |      | 67 |      | 99  |      |
| 4  |            | 36 |      | 68 |      | 100 |      |
| 5  |            | 37 |      | 69 |      | 101 |      |
| 6  |            | 38 |      | 70 |      | 102 |      |
| 7  |            | 39 |      | 71 |      | 103 |      |
| 8  |            |    |      |    |      | 104 |      |
| 9  |            |    |      |    |      | 105 |      |
| 10 |            |    |      |    |      | 106 | usb  |
| 11 | SATA       |    |      |    |      | 107 | usb  |
| 12 | SATA       |    |      |    |      | 108 |      |
| 13 |            |    |      |    |      | 109 | usb  |
| 14 | SATA       |    |      |    |      | 110 | usb  |
| 15 | SATA       |    |      |    |      |     |      |
| 16 |            |    |      |    |      |     |      |
| 17 |            |    |      |    |      |     |      |
| 18 |            |    |      |    |      |     |      |
| 19 |            |    |      |    |      |     |      |
| 20 |            |    |      |    |      |     |      |
| 21 |            |    |      |    |      |     |      |
| 22 |            |    |      |    |      |     |      |
| 23 |            |    |      |    |      |     |      |
| 24 | SAR_GPIO1  |    |      |    |      |     |      |
| 25 | SAR_GPIO0? |    |      |    |      |     |      |
| 26 |            |    |      |    |      |     |      |
| 27 |            |    |      |    |      |     |      |
| 28 |            |    |      |    |      |     |      |
| 29 |            |    |      |    |      |     |      |
| 30 |            |    |      |    |      |     |      |
| 31 |            |    |      |    |      |     |      |
| 32 |            |    |      |    |      |     |      |

## Boot strap pins

| boot device | PM_SPI_CK |
|-------------|-----------|
| SPI NOR     | 0         |
| SPI NAND    | 1         |

| secure boot| PM_SPI_DI |
|------------|-----------|
| on         | 0         |
| off        | 1         |

| boot ?? | PM_SPI_WPZ |
|---------|------------|
| NOR     | 0          |
| ROM     | 1          |
