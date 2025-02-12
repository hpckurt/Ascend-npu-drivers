# Ascend-npu-drivers
Drivers and NPU firmware for the Huawei Ascend cards (so you don't need a Chinese phone number to use an NPU card!)

Huawei Atlas drivers are extremely difficult to obtain unless you have a Chinese phone number. I've uploaded the drivers here.

Drivers tested on Ubuntu 20.04 WITHOUT the HWE kernel. No support will be given, use at your own risk, etc.

**NOTE**: The A300 (3000) will only work on ARM64 machines (like the 飞腾D2000)

# Installing Drivers

Installing the drivers is slightly different from other accelerators. Instead of installing the firmware first, you install it *after* the driver.

Here are the steps to getting a functional NPU install:

```
1. apt install dkms linux-headers-$(uname -r)
2. chmod +x <driver name>.run
3. ./<driver name>.run --full --install-for-all
4. ./<npu firmware>.run --full
5. reboot
```
After a restart, you should see the NPU device show up when running `npu-smi info`:

```
+--------------------------------------------------------------------------------------------------------+
| npu-smi 23.0.0                                   Version: 23.0.0                                       |
+-------------------------------+-----------------+------------------------------------------------------+
| NPU     Name                  | Health          | Power(W)     Temp(C)           Hugepages-Usage(page) |
| Chip    Device                | Bus-Id          | AICore(%)    Memory-Usage(MB)                        |
+===============================+=================+======================================================+
| 0       310                   | OK              | 12.8         61                0     / 969           |
| 0       0                     | 0000:01:00.0    | 0            577  / 7759                             |
+===============================+=================+======================================================+
+-------------------------------+-----------------+------------------------------------------------------+
| NPU     Chip                  | Process id      | Process name             | Process memory(MB)        |
+===============================+=================+======================================================+
| No running processes found in NPU 0                                                                    |
+===============================+=================+======================================================+
```

