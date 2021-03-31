# Quantizing and Compiling TensorFlow 2 Models
## Description
This tutorial lists the steps to quantize and compile a TensorFlow 2 model into XRT graph that can run on the DPU of the Ultra96v2 board.

## Pre-requisite
- [Install Docker](../install_docker/install_docker.md)

## Requirements
- TensorFlow 2 floating-point model in `h5` format (we will refer to it as `float_model.h5`).
- Training and test datasets. Those are needed to ensure that there is no loss in accuracy in the quantization step.
- The architecture file (`arch.json`) for the hardware platform. For the pre-built SD card image for the Ultra96v2 in Mario's [Vitis-AI 1.3](https://www.hackster.io/AlbertaBeef/vitis-ai-1-3-flow-for-avnet-vitis-platforms-cd0c51) tutorial, this file can be found in the BOOT partition.

## Steps
0. If you have not done so already, open up a terminal and install `git`:
    ```
    sudo apt install git
    ```
1. Open up a terminal and clone version 1.3 of Vitis-AI's github repository:
    ```bash
    mkdir -p ~/project/2020.2
    cd ~/project/2020.2
    git clone -b v1.3 https://github.com/Xilinx/Vitis-AI
    cd Vitis-AI
    ```
2. Pull version 1.3.411 of the docker container with the following command:
    ```bash
    docker pull xilinx/vitis-ai:1.3.411
    ```
3. Launch version 1.3.411 of the Vitis-AI docker from the Vitis-AI directory:
    ```bash
    sh -x docker_run.sh xilinx/vitis-ai:1.3.411
    ```
    Press `y` to agree to the Vitis-AI's license terms. NOTE: The following steps assume that you will run the terminal commands in this docker container.
4. Create a directory for your model:
    ```bash
    cd models
    mkdir <your model name>
    cd <your model name>
    ```
    NOTE: `<your model name>` should not contain spaces.
5. Copy your model and architecture files and training and testing datasets to your directory:
    ```bash
    cp <path to model file> float_model.h5
    cp <path to arch.json file> .
    mkdir train test
    cp <path to train dataset>/* train
    cp <path to test dataset>/* test
    ```
6. Your current directory structure should look like the one below:
    ```
    Vitis-AI
    |-- models
        |-- <your model name>
            |-- arch.json
            |-- float_model.h5
            |-- test
            |   |-- test dataset files
            |-- train
                |-- train dataset files
    ```
7. Create a python script to quantize the model. Call it `quantize.py`.
    ```bash
    touch quantize.py
    ```
8. Copy the code below to `quantize.py`:
    ```python
    import tensorflow as tf
    from tensorflow_model_optimization.quantization.keras import vitis_quantize

    # Quantize and calibrate the the floating point model
    float_model = tf.keras.models.load_model('float_model.h5')
    quantizer = vitis_quantize.VitisQuantizer(float_model)
    quantized_model = quantizer.quantize_model(calib_dataset=calib_dataset)

    # Save the model
    quantized_model.save('quantized_model.h5')

    # Evaluate the quantized model
    with vitis_quantize.quantize_scope():
      quantized_model = tf.keras.models.load_model('quantized_model.h5')
      quantized_model.compile(loss=tf.keras.losses.SparseCategoricalCrossentropy(),
        metrics=tf.keras.metrics.SparseTopKCategoricalAccuracy())
      quantized_model.evaluate(eval_dataset)
    ```
     `calib_dataset` and `eval_dataset` should contain train and test datasets, respectively. The two datasets should be pre-processed and have the same shape as the testing dataset used to evaluate the original floating-point model.
9. Run the following commands to quantize the model (using `quantize.py` script) and compile it:
    ```bash
    conda activate vitis-ai-tensorflow2
    python3 quantize.py
    vai_c_tensorflow2 --model quantized_model.h5 --arch arch.json --output_dir xmodel --net_name <your model name>
    ```
    NOTE: `<your model name>` should not contain spaces.
10. Your final directory structure should look like the one below:
    ```
    Vitis-AI
    |-- models
        |-- <your model name>
            |-- arch.json
            |-- float_model.h5
            |-- quantized_model.h5
            |-- quantize.py
            |-- test
            |   |-- test dataset files
            |-- train
            |   |-- train dataset files
            |-- xmodel
                |-- <your model name>_org.xmodel
                |-- <your model name>.xmodel
                |-- md5sum.txt
                |-- meta.json
    ```

## Next Steps
Now that you have quantized and compiled model, copy `xmodel` directory into the SD card on the Ultra96v2 and follow the instructions in [Running a quantized model in the Ultra96v2](TODO).
