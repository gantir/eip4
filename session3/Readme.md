## Summary
* The accuracy of 83.96 was achieved on this file [https://github.com/gantir/eip4/blob/master/session3/assign_3.ipynb]
* The above was achieved with 74,597 parameters of which 73,317 are trainable.
* This same model without data augumentation resulted highest accuracy of 81.77
* I tried different networks which got to lesser accuracy than this network with 98K+ parameters. In one of the trail runs I got to a network with about 65K+ parameters which could beat the seed program accuracy, but it's performance was poor to this network. However, I missed storing the model defenition and hence could not try how it's behavior would be with data augumentation.

## Details
* Final Validation accuracy for Base Network
  * Accuracy on test data is: 83.60
* Your model definition (model.add... ) with output channel size and receptive field
```
my_model = Sequential()

my_model.add(SeparableConvolution2D(64, 3, 3, border_mode='same', input_shape=(32, 32, 3), activation='relu')) # 32*32*64, rf: 3
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(64, 3, 3, border_mode='valid', activation='relu')) # 30*30*64, rf: 5
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(MaxPooling2D(pool_size=(2, 2))) # 15*15*64, rf: 9
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(128, 3, 3, border_mode='same', activation='relu')) # 15*15*128, rf: 13
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(128, 3, 3, border_mode='valid', activation='relu')) # 13*13*128 rf: 17
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(MaxPooling2D(pool_size=(2, 2))) # 6*6*128 rf: 25
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(128, 3, 3, border_mode='same', activation='relu')) # 6*6*128 rf: 33
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(SeparableConvolution2D(128, 3, 3, border_mode='valid', activation='relu')) # 4*4*128 rf: 41
my_model.add(BatchNormalization())
my_model.add(Dropout(0.1))

my_model.add(AveragePooling2D()) # 2*2*128 rf: ? 
my_model.add(Flatten()) # 512, rf: ?
my_model.add(Dense(num_classes, activation='softmax'))

# Compile the model
my_model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
```
* Your 50 epoch logs
  * Epoch 1/50
781/781 [==============================] - 49s 63ms/step - loss: 1.5242 - acc: 0.4515 - val_loss: 1.2618 - val_acc: 0.5666
  * Epoch 2/50
781/781 [==============================] - 46s 59ms/step - loss: 1.1929 - acc: 0.5755 - val_loss: 1.0828 - val_acc: 0.6210
  * Epoch 3/50
781/781 [==============================] - 46s 59ms/step - loss: 1.0567 - acc: 0.6265 - val_loss: 1.0791 - val_acc: 0.6447
  * Epoch 4/50
781/781 [==============================] - 46s 59ms/step - loss: 0.9630 - acc: 0.6602 - val_loss: 0.8587 - val_acc: 0.7033
  * Epoch 5/50
781/781 [==============================] - 46s 59ms/step - loss: 0.8983 - acc: 0.6833 - val_loss: 0.8271 - val_acc: 0.7172
  * Epoch 6/50
781/781 [==============================] - 46s 59ms/step - loss: 0.8555 - acc: 0.6994 - val_loss: 0.7568 - val_acc: 0.7446
  * Epoch 7/50
781/781 [==============================] - 46s 59ms/step - loss: 0.8197 - acc: 0.7130 - val_loss: 0.7577 - val_acc: 0.7379
  * Epoch 8/50
781/781 [==============================] - 46s 59ms/step - loss: 0.7893 - acc: 0.7255 - val_loss: 0.7474 - val_acc: 0.7511
  * Epoch 9/50
781/781 [==============================] - 46s 59ms/step - loss: 0.7640 - acc: 0.7317 - val_loss: 0.6828 - val_acc: 0.7703
  * Epoch 10/50
781/781 [==============================] - 46s 59ms/step - loss: 0.7379 - acc: 0.7430 - val_loss: 0.6856 - val_acc: 0.7675
  * Epoch 11/50
781/781 [==============================] - 46s 59ms/step - loss: 0.7173 - acc: 0.7500 - val_loss: 0.6724 - val_acc: 0.7708
  * Epoch 12/50
781/781 [==============================] - 46s 59ms/step - loss: 0.7022 - acc: 0.7552 - val_loss: 0.6639 - val_acc: 0.7813
  * Epoch 13/50
781/781 [==============================] - 46s 59ms/step - loss: 0.6889 - acc: 0.7615 - val_loss: 0.6900 - val_acc: 0.7702
  * Epoch 14/50
781/781 [==============================] - 46s 59ms/step - loss: 0.6738 - acc: 0.7648 - val_loss: 0.6710 - val_acc: 0.7772
  * Epoch 15/50
781/781 [==============================] - 46s 59ms/step - loss: 0.6575 - acc: 0.7718 - val_loss: 0.6732 - val_acc: 0.7747
  * Epoch 16/50
781/781 [==============================] - 46s 58ms/step - loss: 0.6503 - acc: 0.7735 - val_loss: 0.6567 - val_acc: 0.7824
  * Epoch 17/50
781/781 [==============================] - 46s 59ms/step - loss: 0.6375 - acc: 0.7782 - val_loss: 0.5947 - val_acc: 0.8014
  * Epoch 18/50
781/781 [==============================] - 46s 59ms/step - loss: 0.6310 - acc: 0.7811 - val_loss: 0.5934 - val_acc: 0.7978
  * Epoch 19/50
781/781 [==============================] - 46s 59ms/step - loss: 0.6176 - acc: 0.7839 - val_loss: 0.6259 - val_acc: 0.7937
  * Epoch 20/50
781/781 [==============================] - 46s 59ms/step - loss: 0.6132 - acc: 0.7872 - val_loss: 0.6201 - val_acc: 0.7908
  * Epoch 21/50
781/781 [==============================] - 46s 58ms/step - loss: 0.6058 - acc: 0.7899 - val_loss: 0.5392 - val_acc: 0.8126
  * Epoch 22/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5991 - acc: 0.7914 - val_loss: 0.5858 - val_acc: 0.8021
  * Epoch 23/50
781/781 [==============================] - 46s 58ms/step - loss: 0.5905 - acc: 0.7929 - val_loss: 0.6164 - val_acc: 0.8005
  * Epoch 24/50
781/781 [==============================] - 49s 62ms/step - loss: 0.5884 - acc: 0.7945 - val_loss: 0.5538 - val_acc: 0.8147
  * Epoch 25/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5870 - acc: 0.7975 - val_loss: 0.5486 - val_acc: 0.8154
  * Epoch 26/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5745 - acc: 0.7996 - val_loss: 0.5530 - val_acc: 0.8154
  * Epoch 27/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5649 - acc: 0.8022 - val_loss: 0.5063 - val_acc: 0.8255
  * Epoch 28/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5650 - acc: 0.8024 - val_loss: 0.5928 - val_acc: 0.8022
  * Epoch 29/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5603 - acc: 0.8046 - val_loss: 0.5697 - val_acc: 0.8065
  * Epoch 30/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5538 - acc: 0.8059 - val_loss: 0.5720 - val_acc: 0.8115
  * Epoch 31/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5454 - acc: 0.8101 - val_loss: 0.5560 - val_acc: 0.8158
  * Epoch 32/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5455 - acc: 0.8112 - val_loss: 0.5130 - val_acc: 0.8289
  * Epoch 33/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5402 - acc: 0.8098 - val_loss: 0.5317 - val_acc: 0.8175
  * Epoch 34/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5348 - acc: 0.8130 - val_loss: 0.5453 - val_acc: 0.8152
  * Epoch 35/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5275 - acc: 0.8166 - val_loss: 0.4845 - val_acc: 0.8347
  * Epoch 36/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5342 - acc: 0.8121 - val_loss: 0.5180 - val_acc: 0.8243
  * Epoch 37/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5265 - acc: 0.8162 - val_loss: 0.5939 - val_acc: 0.8071
  * Epoch 38/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5241 - acc: 0.8166 - val_loss: 0.5332 - val_acc: 0.8202
  * Epoch 39/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5232 - acc: 0.8158 - val_loss: 0.5285 - val_acc: 0.8265
  * Epoch 40/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5155 - acc: 0.8214 - val_loss: 0.4961 - val_acc: 0.8300
  * Epoch 41/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5150 - acc: 0.8194 - val_loss: 0.5106 - val_acc: 0.8290
  * Epoch 42/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5094 - acc: 0.8213 - val_loss: 0.5551 - val_acc: 0.8121
  * Epoch 43/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5047 - acc: 0.8271 - val_loss: 0.4735 - val_acc: 0.8396
  * Epoch 44/50
781/781 [==============================] - 47s 60ms/step - loss: 0.5012 - acc: 0.8261 - val_loss: 0.5163 - val_acc: 0.8256
  * Epoch 45/50
781/781 [==============================] - 47s 60ms/step - loss: 0.4975 - acc: 0.8249 - val_loss: 0.5158 - val_acc: 0.8270
  * Epoch 46/50
781/781 [==============================] - 47s 60ms/step - loss: 0.4951 - acc: 0.8282 - val_loss: 0.5571 - val_acc: 0.8121
  * Epoch 47/50
781/781 [==============================] - 47s 60ms/step - loss: 0.4978 - acc: 0.8262 - val_loss: 0.5042 - val_acc: 0.8276
  * Epoch 48/50
781/781 [==============================] - 47s 60ms/step - loss: 0.4939 - acc: 0.8280 - val_loss: 0.4879 - val_acc: 0.8390
  * Epoch 49/50
781/781 [==============================] - 47s 60ms/step - loss: 0.4870 - acc: 0.8300 - val_loss: 0.4774 - val_acc: 0.8366
  * Epoch 50/50
781/781 [==============================] - 47s 60ms/step - loss: 0.4842 - acc: 0.8315 - val_loss: 0.4692 - val_acc: 0.8360

Model took 2327.07 seconds to train
