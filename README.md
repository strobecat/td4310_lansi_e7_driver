# td4310_lansi_e7_driver

Touchscreen driver found in downstream 4.9 kernel with build errors fixed when compiling with mainline kernel

## Usage
Put files under `drivers/input/touchscreen/td4310_lansi_e7` then  
```diff
diff --git a/drivers/input/touchscreen/Kconfig b/drivers/input/touchscreen/Kconfig
index 91a2b584d..325fa14ec 100644
--- a/drivers/input/touchscreen/Kconfig
+++ b/drivers/input/touchscreen/Kconfig
@@ -1403,4 +1403,6 @@ config TOUCHSCREEN_HIMAX_HX83112B
 	  To compile this driver as a module, choose M here: the
 	  module will be called himax_hx83112b.
 
+source "drivers/input/touchscreen/td4310_lansi_e7/Kconfig"
+
 endif
diff --git a/drivers/input/touchscreen/Makefile b/drivers/input/touchscreen/Makefile
index 97a025c6a..48f26e212 100644
--- a/drivers/input/touchscreen/Makefile
+++ b/drivers/input/touchscreen/Makefile
@@ -118,3 +118,4 @@ obj-$(CONFIG_TOUCHSCREEN_IQS5XX)	+= iqs5xx.o
 obj-$(CONFIG_TOUCHSCREEN_IQS7211)	+= iqs7211.o
 obj-$(CONFIG_TOUCHSCREEN_ZINITIX)	+= zinitix.o
 obj-$(CONFIG_TOUCHSCREEN_HIMAX_HX83112B)	+= himax_hx83112b.o
+obj-$(CONFIG_TOUCHSCREEN_SYNAPTICS_DSX)         += td4310_lansi_e7/
```
and config  
```makefile
CONFIG_TOUCHSCREEN_SYNAPTICS_DSX=y
CONFIG_TOUCHSCREEN_SYNAPTICS_DSX_I2C=m
CONFIG_TOUCHSCREEN_SYNAPTICS_DSX_CORE=m
CONFIG_TOUCHSCREEN_SYNAPTICS_DSX_RMI_DEV=m
CONFIG_TOUCHSCREEN_SYNAPTICS_DSX_FW_UPDATE=m
CONFIG_TOUCHSCREEN_SYNAPTICS_DSX_TEST_REPORTING=m
```
then merge dts
