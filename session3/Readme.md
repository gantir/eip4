## Summary
* The accuracy of 85.97 was achieved on this file [https://github.com/gantir/eip4/blob/master/session3/assign_3_submission.ipynb] with 99,445 params of which 98K are trainable. The final accuracy was 85.86. The difference with this model was this had variable learning rate
* The accuracy of 84.29 was achieved on this file [https://github.com/gantir/eip4/blob/9841f3a6f54402b47fe52681274259faaadefd71/session3/assign_3.ipynb] with 73,957 params of which 72,677 are trainable. The final accuracy was 83.84
* I tried different networks which got to lesser accuracy than this network with 98K+ parameters. In one of the trail runs I got to a network with about 65K+ parameters which could beat the seed program accuracy, but it's performance was poor to this network. However, I missed storing the model defenition and hence could not try how it's behavior would be with data augumentation.

## Details
* Final Validation accuracy for Base Network (https://github.com/gantir/eip4/blob/master/session3/assign_3_submission.ipynb)
  * Accuracy on test data is: 85.86
* Your model definition (model.add... ) with output channel size and receptive field
```
my_model = Sequential()

my_model.add(SeparableConvolution2D(64, 3, 3, border_mode='same', input_shape=(32, 32, 3), activation='relu', use_bias=False)) # 32*32*64, rf: 3
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(64, 3, 3, border_mode='valid', activation='relu', use_bias=False)) # 30*30*64, rf: 5
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(MaxPooling2D(pool_size=(2, 2))) # 15*15*64, rf: 9
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(128, 3, 3, border_mode='same', activation='relu', use_bias=False)) # 15*15*128, rf: 13
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(128, 3, 3, border_mode='valid', activation='relu', use_bias=False)) # 13*13*128 rf: 17
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(MaxPooling2D(pool_size=(2, 2))) # 6*6*128 rf: 25
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(128, 3, 3, border_mode='same', activation='relu', use_bias=False)) # 6*6*128 rf: 33
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(128, 3, 3, border_mode='valid', activation='relu', use_bias=False)) # 4*4*128 rf: 41
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(AveragePooling2D()) # 2*2*128 rf: ? 
my_model.add(Flatten()) # 512, rf: ?

my_model.add(Dense(num_classes, activation='softmax'))

# Compile the model
my_model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
```
* Your 50 epoch logs
```
Epoch 1/50

Epoch 00001: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 58s 149ms/step - loss: 1.5557 - acc: 0.4373 - val_loss: 1.4361 - val_acc: 0.5415
Epoch 2/50

Epoch 00002: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 1.1925 - acc: 0.5738 - val_loss: 1.1993 - val_acc: 0.5945
Epoch 3/50

Epoch 00003: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 1.0417 - acc: 0.6285 - val_loss: 1.0687 - val_acc: 0.6524
Epoch 4/50

Epoch 00004: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.9511 - acc: 0.6644 - val_loss: 0.9113 - val_acc: 0.6927
Epoch 5/50

Epoch 00005: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.8848 - acc: 0.6886 - val_loss: 0.8235 - val_acc: 0.7107
Epoch 6/50

Epoch 00006: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.8382 - acc: 0.7048 - val_loss: 0.7792 - val_acc: 0.7362
Epoch 7/50

Epoch 00007: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.7982 - acc: 0.7199 - val_loss: 0.7395 - val_acc: 0.7438
Epoch 8/50

Epoch 00008: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.7557 - acc: 0.7351 - val_loss: 0.7790 - val_acc: 0.7412
Epoch 9/50

Epoch 00009: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.7284 - acc: 0.7459 - val_loss: 0.7304 - val_acc: 0.7532
Epoch 10/50

Epoch 00010: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.7134 - acc: 0.7513 - val_loss: 0.6800 - val_acc: 0.7726
Epoch 11/50

Epoch 00011: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.6872 - acc: 0.7598 - val_loss: 0.6862 - val_acc: 0.7683
Epoch 12/50

Epoch 00012: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.6756 - acc: 0.7645 - val_loss: 0.7042 - val_acc: 0.7661
Epoch 13/50

Epoch 00013: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.6504 - acc: 0.7739 - val_loss: 0.5856 - val_acc: 0.8024
Epoch 14/50

Epoch 00014: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 52s 133ms/step - loss: 0.6306 - acc: 0.7791 - val_loss: 0.6116 - val_acc: 0.7919
Epoch 15/50

Epoch 00015: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.6247 - acc: 0.7830 - val_loss: 0.6492 - val_acc: 0.7874
Epoch 16/50

Epoch 00016: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.6119 - acc: 0.7852 - val_loss: 0.5855 - val_acc: 0.8039
Epoch 17/50

Epoch 00017: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5965 - acc: 0.7922 - val_loss: 0.6048 - val_acc: 0.8000
Epoch 18/50

Epoch 00018: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5893 - acc: 0.7952 - val_loss: 0.5782 - val_acc: 0.8048
Epoch 19/50

Epoch 00019: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5768 - acc: 0.7986 - val_loss: 0.7024 - val_acc: 0.7748
Epoch 20/50

Epoch 00020: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5700 - acc: 0.8018 - val_loss: 0.6498 - val_acc: 0.7898
Epoch 21/50

Epoch 00021: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5562 - acc: 0.8066 - val_loss: 0.5830 - val_acc: 0.8055
Epoch 22/50

Epoch 00022: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5500 - acc: 0.8074 - val_loss: 0.6385 - val_acc: 0.7967
Epoch 23/50

Epoch 00023: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5422 - acc: 0.8119 - val_loss: 0.5620 - val_acc: 0.8101
Epoch 24/50

Epoch 00024: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5399 - acc: 0.8122 - val_loss: 0.5218 - val_acc: 0.8270
Epoch 25/50

Epoch 00025: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5345 - acc: 0.8123 - val_loss: 0.5354 - val_acc: 0.8197
Epoch 26/50

Epoch 00026: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5185 - acc: 0.8199 - val_loss: 0.5285 - val_acc: 0.8251
Epoch 27/50

Epoch 00027: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5160 - acc: 0.8196 - val_loss: 0.5104 - val_acc: 0.8308
Epoch 28/50

Epoch 00028: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5076 - acc: 0.8235 - val_loss: 0.5193 - val_acc: 0.8229
Epoch 29/50

Epoch 00029: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.5084 - acc: 0.8217 - val_loss: 0.4858 - val_acc: 0.8354
Epoch 30/50

Epoch 00030: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.4962 - acc: 0.8258 - val_loss: 0.5025 - val_acc: 0.8300
Epoch 31/50

Epoch 00031: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.4956 - acc: 0.8273 - val_loss: 0.5164 - val_acc: 0.8296
Epoch 32/50

Epoch 00032: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.4901 - acc: 0.8272 - val_loss: 0.5167 - val_acc: 0.8281
Epoch 33/50

Epoch 00033: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.4877 - acc: 0.8302 - val_loss: 0.4924 - val_acc: 0.8374
Epoch 34/50

Epoch 00034: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.4775 - acc: 0.8336 - val_loss: 0.4772 - val_acc: 0.8394
Epoch 35/50

Epoch 00035: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.4805 - acc: 0.8332 - val_loss: 0.4876 - val_acc: 0.8343
Epoch 36/50

Epoch 00036: LearningRateScheduler setting learning rate to 0.001.
390/390 [==============================] - 51s 130ms/step - loss: 0.4775 - acc: 0.8338 - val_loss: 0.4590 - val_acc: 0.8479
Epoch 37/50

Epoch 00037: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4399 - acc: 0.8485 - val_loss: 0.4574 - val_acc: 0.8473
Epoch 38/50

Epoch 00038: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4317 - acc: 0.8486 - val_loss: 0.4420 - val_acc: 0.8557
Epoch 39/50

Epoch 00039: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 131ms/step - loss: 0.4296 - acc: 0.8508 - val_loss: 0.4718 - val_acc: 0.8473
Epoch 40/50

Epoch 00040: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4260 - acc: 0.8526 - val_loss: 0.4652 - val_acc: 0.8474
Epoch 41/50

Epoch 00041: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4213 - acc: 0.8520 - val_loss: 0.4234 - val_acc: 0.8597
Epoch 42/50

Epoch 00042: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4243 - acc: 0.8515 - val_loss: 0.4496 - val_acc: 0.8521
Epoch 43/50

Epoch 00043: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4212 - acc: 0.8524 - val_loss: 0.4485 - val_acc: 0.8518
Epoch 44/50

Epoch 00044: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4135 - acc: 0.8568 - val_loss: 0.4483 - val_acc: 0.8548
Epoch 45/50

Epoch 00045: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4084 - acc: 0.8556 - val_loss: 0.4329 - val_acc: 0.8560
Epoch 46/50

Epoch 00046: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4097 - acc: 0.8578 - val_loss: 0.4330 - val_acc: 0.8581
Epoch 47/50

Epoch 00047: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4078 - acc: 0.8569 - val_loss: 0.4666 - val_acc: 0.8483
Epoch 48/50

Epoch 00048: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 131ms/step - loss: 0.4090 - acc: 0.8565 - val_loss: 0.4320 - val_acc: 0.8585
Epoch 49/50

Epoch 00049: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4065 - acc: 0.8577 - val_loss: 0.4428 - val_acc: 0.8583
Epoch 50/50

Epoch 00050: LearningRateScheduler setting learning rate to 0.0005.
390/390 [==============================] - 51s 130ms/step - loss: 0.4009 - acc: 0.8598 - val_loss: 0.4421 - val_acc: 0.8586

Model took 2559.65 seconds to train
```
