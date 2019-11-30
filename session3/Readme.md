## Summary
* The accuracy of 84.84 was achieved on this file [https://github.com/gantir/eip4/blob/master/session3/assign_3_submission.ipynb] with 99,445 params of which 98K are trainable. The final accuracy was 83.95
* The accuracy of 84.29 was achieved on this file [https://github.com/gantir/eip4/blob/master/session3/assign_3_submission.ipynb] with 73,957 params of which 72,677 are trainable. The final accuracy was 83.84
* I tried different networks which got to lesser accuracy than this network with 98K+ parameters. In one of the trail runs I got to a network with about 65K+ parameters which could beat the seed program accuracy, but it's performance was poor to this network. However, I missed storing the model defenition and hence could not try how it's behavior would be with data augumentation.

## Details
* Final Validation accuracy for Base Network
  * Accuracy on test data is: 83.84
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
781/781 [==============================] - 58s 74ms/step - loss: 1.5412 - acc: 0.4443 - val_loss: 1.2130 - val_acc: 0.5790
Epoch 2/50
781/781 [==============================] - 52s 67ms/step - loss: 1.1981 - acc: 0.5733 - val_loss: 1.0689 - val_acc: 0.6358
Epoch 3/50
781/781 [==============================] - 52s 67ms/step - loss: 1.0594 - acc: 0.6241 - val_loss: 0.9519 - val_acc: 0.6720
Epoch 4/50
781/781 [==============================] - 52s 66ms/step - loss: 0.9613 - acc: 0.6596 - val_loss: 0.8576 - val_acc: 0.7039
Epoch 5/50
781/781 [==============================] - 52s 67ms/step - loss: 0.8974 - acc: 0.6830 - val_loss: 0.8559 - val_acc: 0.7117
Epoch 6/50
781/781 [==============================] - 52s 67ms/step - loss: 0.8542 - acc: 0.7005 - val_loss: 0.7628 - val_acc: 0.7349
Epoch 7/50
781/781 [==============================] - 52s 67ms/step - loss: 0.8243 - acc: 0.7119 - val_loss: 0.7377 - val_acc: 0.7512
Epoch 8/50
781/781 [==============================] - 52s 66ms/step - loss: 0.7825 - acc: 0.7255 - val_loss: 0.6898 - val_acc: 0.7650
Epoch 9/50
781/781 [==============================] - 51s 66ms/step - loss: 0.7573 - acc: 0.7334 - val_loss: 0.7058 - val_acc: 0.7599
Epoch 10/50
781/781 [==============================] - 52s 66ms/step - loss: 0.7418 - acc: 0.7398 - val_loss: 0.6992 - val_acc: 0.7630
Epoch 11/50
781/781 [==============================] - 52s 66ms/step - loss: 0.7232 - acc: 0.7490 - val_loss: 0.6782 - val_acc: 0.7698
Epoch 12/50
781/781 [==============================] - 52s 67ms/step - loss: 0.7118 - acc: 0.7524 - val_loss: 0.6203 - val_acc: 0.7887
Epoch 13/50
781/781 [==============================] - 53s 68ms/step - loss: 0.6920 - acc: 0.7588 - val_loss: 0.6559 - val_acc: 0.7799
Epoch 14/50
781/781 [==============================] - 52s 67ms/step - loss: 0.6800 - acc: 0.7613 - val_loss: 0.6368 - val_acc: 0.7811
Epoch 15/50
781/781 [==============================] - 52s 67ms/step - loss: 0.6639 - acc: 0.7703 - val_loss: 0.6375 - val_acc: 0.7817
Epoch 16/50
781/781 [==============================] - 52s 67ms/step - loss: 0.6538 - acc: 0.7696 - val_loss: 0.6433 - val_acc: 0.7862
Epoch 17/50
781/781 [==============================] - 52s 67ms/step - loss: 0.6440 - acc: 0.7753 - val_loss: 0.6651 - val_acc: 0.7711
Epoch 18/50
781/781 [==============================] - 52s 67ms/step - loss: 0.6358 - acc: 0.7779 - val_loss: 0.6166 - val_acc: 0.7906
Epoch 19/50
781/781 [==============================] - 52s 67ms/step - loss: 0.6248 - acc: 0.7818 - val_loss: 0.6315 - val_acc: 0.7875
Epoch 20/50
781/781 [==============================] - 52s 67ms/step - loss: 0.6169 - acc: 0.7866 - val_loss: 0.5951 - val_acc: 0.7991
Epoch 21/50
781/781 [==============================] - 53s 67ms/step - loss: 0.6014 - acc: 0.7897 - val_loss: 0.6003 - val_acc: 0.7989
Epoch 22/50
781/781 [==============================] - 53s 67ms/step - loss: 0.6008 - acc: 0.7905 - val_loss: 0.5958 - val_acc: 0.8003
Epoch 23/50
781/781 [==============================] - 53s 67ms/step - loss: 0.5988 - acc: 0.7888 - val_loss: 0.5984 - val_acc: 0.8015
Epoch 24/50
781/781 [==============================] - 53s 67ms/step - loss: 0.5884 - acc: 0.7932 - val_loss: 0.5489 - val_acc: 0.8163
Epoch 25/50
781/781 [==============================] - 53s 68ms/step - loss: 0.5854 - acc: 0.7952 - val_loss: 0.5665 - val_acc: 0.8094
Epoch 26/50
781/781 [==============================] - 53s 68ms/step - loss: 0.5823 - acc: 0.7969 - val_loss: 0.5679 - val_acc: 0.8054
Epoch 27/50
781/781 [==============================] - 53s 67ms/step - loss: 0.5754 - acc: 0.7977 - val_loss: 0.5331 - val_acc: 0.8200
Epoch 28/50
781/781 [==============================] - 52s 67ms/step - loss: 0.5578 - acc: 0.8057 - val_loss: 0.5473 - val_acc: 0.8146
Epoch 29/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5657 - acc: 0.8047 - val_loss: 0.5536 - val_acc: 0.8139
Epoch 30/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5533 - acc: 0.8056 - val_loss: 0.5380 - val_acc: 0.8163
Epoch 31/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5529 - acc: 0.8062 - val_loss: 0.5484 - val_acc: 0.8145
Epoch 32/50
781/781 [==============================] - 52s 67ms/step - loss: 0.5498 - acc: 0.8066 - val_loss: 0.5818 - val_acc: 0.8047
Epoch 33/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5456 - acc: 0.8079 - val_loss: 0.5368 - val_acc: 0.8168
Epoch 34/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5353 - acc: 0.8140 - val_loss: 0.5368 - val_acc: 0.8221
Epoch 35/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5388 - acc: 0.8104 - val_loss: 0.5663 - val_acc: 0.8133
Epoch 36/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5349 - acc: 0.8121 - val_loss: 0.5231 - val_acc: 0.8268
Epoch 37/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5322 - acc: 0.8134 - val_loss: 0.5381 - val_acc: 0.8222
Epoch 38/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5217 - acc: 0.8169 - val_loss: 0.5274 - val_acc: 0.8240
Epoch 39/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5226 - acc: 0.8174 - val_loss: 0.5851 - val_acc: 0.8039
Epoch 40/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5236 - acc: 0.8181 - val_loss: 0.6263 - val_acc: 0.7924
Epoch 41/50
781/781 [==============================] - 52s 66ms/step - loss: 0.5180 - acc: 0.8193 - val_loss: 0.5126 - val_acc: 0.8301
Epoch 42/50
781/781 [==============================] - 51s 65ms/step - loss: 0.5095 - acc: 0.8204 - val_loss: 0.5202 - val_acc: 0.8247
Epoch 43/50
781/781 [==============================] - 51s 65ms/step - loss: 0.5094 - acc: 0.8213 - val_loss: 0.5574 - val_acc: 0.8158
Epoch 44/50
781/781 [==============================] - 51s 65ms/step - loss: 0.5024 - acc: 0.8251 - val_loss: 0.4919 - val_acc: 0.8374
Epoch 45/50
781/781 [==============================] - 51s 65ms/step - loss: 0.5052 - acc: 0.8251 - val_loss: 0.4680 - val_acc: 0.8429
Epoch 46/50
781/781 [==============================] - 51s 66ms/step - loss: 0.4982 - acc: 0.8245 - val_loss: 0.5155 - val_acc: 0.8258
Epoch 47/50
781/781 [==============================] - 51s 65ms/step - loss: 0.5012 - acc: 0.8241 - val_loss: 0.4832 - val_acc: 0.8342
Epoch 48/50
781/781 [==============================] - 51s 65ms/step - loss: 0.4979 - acc: 0.8256 - val_loss: 0.5653 - val_acc: 0.8096
Epoch 49/50
781/781 [==============================] - 51s 65ms/step - loss: 0.4937 - acc: 0.8268 - val_loss: 0.5360 - val_acc: 0.8240
Epoch 50/50
781/781 [==============================] - 51s 66ms/step - loss: 0.4901 - acc: 0.8283 - val_loss: 0.4871 - val_acc: 0.8384

Model took 2602.76 seconds to train
```
