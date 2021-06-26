# Remote-Object-Detection-with-Google-Coral-and-Sixfab-CORE
In this project, we will perform object detection with Coral on the picture we took on the Raspberry Pi, which we provide cellular connection, and we will do all of these operations remotely and quickly.

Ready? Let's get started! 🚀
## Hardware setup
Here's how and what you're ging to build:
1. Attach the [Telit LE910C1 mini PCIe](https://sixfab.com/product/telit-le910c1-mini-pcie-cat1-lte-module/)(or compatible modules) module to the HAT.

2. Attach the antenna to the mini PCIe module. I recommend sticking the antennas as in the picture.

3. Attach 40 pin header to the [Base HAT](https://sixfab.com/product/raspberry-pi-base-hat-3g-4g-lte-minipcie-cards/) that comes with the HAT and insert the [Sixfab SIM](https://sixfab.com/product/connect-sim-card-for-iot-projects/) to Base HAT.

4. Connect the camera module.

5. Now attach the HAT to the Raspberry Pi.

6. Connect the [micro-USB cable](https://sixfab.com/product/right-angle-micro-usb-cable-usb-2-0-a-male-to-micro-b-cable/) to the HAT and Raspberry Pi.

7. Put it inside the enclosure.

Note: The top cover is not used. You can use it if you want.
8. Now connect the USB Accelerator to your Raspberry Pi using the USB cable.

9. Finally, power up the Raspberry Pi.

## Software Setup Instructions
1. Complete the Sixfab CORE installation.
In my previous project, I explained how to install [Sixfab CORE](https://sixfab.com/sixfab-core/). Click on the link below and follow the installation steps there.[Raspberry Pi Cellular Connection using Sixfab CORE](https://www.hackster.io/ensarkarabudak/raspberry-pi-cellular-connection-using-sixfab-core-845f52)

2. Setting up the camera software
Now you need to enable camera support using the raspi-config program you will have used when you first set up your Raspberry Pi.Use the cursor keys to select and open Interfacing Options, and then select Camera and follow the prompt to enable the camera.

3. Setting up the Coral USB Accelerator
Follow Google's [installation Guide](https://coral.ai/docs/accelerator/get-started/) to setting up the Coral USB Accelerator.Login to Sixfab CORE and open 'remote terminal' after making sure your device's cellular connection.Change to the /home/pi directory.

**Download the code from GitHub:**

mkdir coral && cd coral

git clone https://github.com/google-coral/pycoral.git

cd pycoral

**Download the model and labels:**

bash examples/install_requirements.sh detect_image.py
Take the photo.

sudo raspistill -o image.jpg
>**Troubleshooting**
 If you don't run the command with 'sudo' you may get the following error. One solution is to run it with sudo.* failed to open vchiq instance
4. Run the image detector with the photo.

python3 examples/detect_image.py \
--model test_data/ssd_mobilenet_v2_coco_quant_postprocess_edgetpu.tflite \
--labels test_data/coco_labels.txt \
--input image.jpg

5. You should see results like this:
![ensar_XWlfBBQyVd](https://user-images.githubusercontent.com/56815931/123520960-3fb0ea80-d6d1-11eb-84fb-e545fdd16b65.jpg)

# Congrats!
