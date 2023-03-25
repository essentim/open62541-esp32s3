# open62541-esp32s3
An example to get an opc ua server running on an esp32s3 using the open62541 stack

This is a summary I created for an "esp32-s3-DevKitC-1 v1.1" featuring a ESP32-S3-WROOM-2 with 32 MB Flash and 8 MB Ram:


This tutorial is based on https://github.com/cmbahadir/opcua-esp32 and primarily on https://github.com/Pro/open62541-esp32. Thank you to both authors!

Since the esp32-s3 is only fully supported with sdk 4.4 I checked out this sdk-version (support until 2024) and continued according to https://github.com/Pro/open62541-esp32. FYI: Switch to the examples directory in the SDK, check out Pro's repo and update the submodules

Please mind the following steps, that are in this case specific to the dev board I used:
- Adjust the main.c to this, so it fits the chip I use:
![image](https://user-images.githubusercontent.com/6631567/227711571-69690678-5eef-4a28-88d3-5b8f3e0107df.png)

- export the variable for the chip used for the sdk by:
export IDF_TARGET=esp32s3

Then start the menuconfig by idf.py menuconfig and do the following:

- Setup Wifi credentials here:

![image](https://user-images.githubusercontent.com/6631567/227711327-894c9d63-17b5-45ce-8a21-f598d42527cb.png)

- Setup your Flash Size and Speed Here and enable for my case the octal flash:

 ![image](https://user-images.githubusercontent.com/6631567/227711366-599deaa4-dd4d-44ba-9cfe-b91973d62c4d.png)
 
- Go into Component Config ---> ESP32-S3 Specifics ---> and activate support for external SPI connected FLASH

![image](https://user-images.githubusercontent.com/6631567/227711488-c534c544-ac5f-499e-91d2-fe4a535e4fdd.png)

![image](https://user-images.githubusercontent.com/6631567/227711512-8ba68ebe-aa91-45e7-90f6-dbe50cac4f82.png)

You should now get a succesfull build with:

idf.py build

and should be able to build and flash with idf.py flash
