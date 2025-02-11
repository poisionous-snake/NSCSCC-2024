//---------------------------------------------------------------------------------------------------------------------
//---龙芯
//---体系结构教学试验箱3.0（Artix-7）
//---------------------------------------------------------------------------------------------------------------------

本目录提供实验箱（Artix-7）的教学SoC运行pmon并启动Linux内核的测试。

1.测试项包括：网口、DDR3颗粒、串口、SPI flash、nand flash的测试。

2.测试结果判断：
  可正确运行PMON，并通过网口load Linux内核即说明测试通过。

3.测试程序目录结构
   +--soc_up_33M.bit     : SoC的bit流文件，用于下载到FPGA开发板上。
   |        
   |--gzrom.bin          : PMON编译后的bin文件，烧写到SPI flash上。
   |
   |--vmlinux            : Linux内核编译后的文件，在PMON环境下通过网口load启动

4.测试程序使用方法：
  (1) 烧写gzrom.bin到可插拔SPI flash，并插入到开发板上（注意方向！）；
  (2) 将开发板与主机间的下载线和串口线连接好，
      并使用连接网线，可与主机直连（此时主机需配置IP），或均连入同一局域网。
  (3) 开发板上电，使用Vivado的Open Hardware Manager下载soc_up_33M.bit到开发板上。
  (4) 下载完成后，会自动运行PMON，配置IP，可使用ping确认与主机网络是通的。
  (5) 搭建tftp服务器，laod Linux内核
  (6) 启动内核。
  如果对运行PMON和load内核不清楚的，可参见同目录下的 pmon运行并load内核启动的方法.pdf
