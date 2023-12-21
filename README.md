# VBU-Net_repo
A unique model for breast tumor segmentation

# Objective
Breast cancer is a leading cause of death among women worldwide. Early detection and accurate diagnosis of breast cancer are essential for improving survival rates. Medical imaging techniques , such as mammography, ultrasound, and histopathology, are critical tools for the study of breast cancer. However, manual interpretation of medical images is time-consuming, and the accuracy of human interpretation can vary. Therefore, there is a need to develop automated tools for medical image analysis to improve the accuracy and efficiency of breast cancer diagnosis. Therefore, the problem statement of this study is to develop an accurate breast tumor segmentation model using histopathological images by combining the U-Net architecture with pre-trained VGG19 and BiLSTM layers. The proposed model aims to improve the accuracy and efficiency of breast cancer diagnosis, potentially aiding pathologists in accurately identifying and delineating breast tumors. The performance of the model is evaluated using accuracy and logarithmic loss metrics, and the results are compared with other state-of-the-art segmentation models. The proposed model has the potential to contribute to the development of computer-aided diagnosis systems for breast cancer, improving patient outcomes and survival rates.

# Algorithm for VBU-MNet

Step 1: Begin
        Step 2: Define the function "model"
        Step 3: Create an input layer (256,256, 3) and 
        Step 4: Load the VGG19 model 
        Step 5: Get the output of the VGG19 model                                               
                      "block5_conv4"
        Step 6: Define skip connection layer names, 
                     ["block4_conv3","block3_conv3",
                       "block2_conv2", "block1_conv2"]
        Step 7: Create an empty list called "skip connections"
        Step 8: Loop through the skip connection layer names 
                    and append the output of each layer to the 
                    "skip connections" list
        Step 9: Define a list of filter sizes, [16, 32, 48, 64]
        Step 10: Set "x" as the "encoder output"
        Step 11: for the filter sizes:
                        a. Up sample "x" using the UpSampling2D
                            layer with a factor of (2,2)
                        b. Concatenate "x" with the corresponding 
                            skip connection layer from 
                            "skip connections"
                        c. Apply a convolutional layer with filter size 
                            "f[i]" and kernel size (3,3) to "x"
                        d. Apply batch normalization to "x"
                        e. Apply ReLU activation to "x"
                        f. Apply another convolutional layer with 
                            "f[i]" and kernel size (3,3) to "x"

                        g. Apply batch normalization to "x"
                        h. Apply ReLU activation to "x"
        Step 12: Apply a convolutional layer with filter size 1 
                        and kernel size (1,1) to "x"
         Step 13: Apply sigmoid activation to "x"

         
        Step 14: Reshape "x" into a 2D tensor with dimensions 
                   (256^2, 1)
        Step 15: Apply a bidirectional LSTM layer with 64 units 
                   and return sequences to "x"
        Step 16: Apply a time-distributed dense layer with 1 unit 
                    and return sequences to "x"
        Step 17: Reshape "x" into a 4D tensor with dimensions 
                   (256,256,1)
        Step 18: Create a model with "input image" as the input 
                     and "x" as the output
        Step 19: Return the mod 

# Conclusion
VBU-Net is an enhanced version of the U-Net architecture that has achieved remarkable results in medical image segmentation tasks, with a Dice coefficient of 0.7981. The key improvements in VBU-Net include the expansion of Vgg19 and BiLstm layers, which allow for more complex feature extraction and capturing of temporal dependencies in the image data. These enhancements make VBU-Net a valuable tool in the clinical field, where accurate image segmentation is crucial for diagnosis and treatment planning.

One of the main advantages of VBU-Net is its ability to accurately segment organs, tumors, and blood vessels, which are critical for the diagnosis and treatment of various diseases. For example, in cancer treatment, precise segmentation of tumors can help oncologists determine the size, shape, and location of tumors, which are important factors in planning radiation therapy or surgical interventions. Accurate segmentation of blood vessels can also aid in the planning of vascular surgeries, such as bypass surgeries or angioplasty.


