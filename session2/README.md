* Training Log:

Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
60000/60000 [==============================] - 11s 176us/step - loss: 0.5959 - acc: 0.8281 - val_loss: 0.1036 - val_acc: 0.9818
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
60000/60000 [==============================] - 6s 96us/step - loss: 0.2743 - acc: 0.9156 - val_loss: 0.0611 - val_acc: 0.9869
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
60000/60000 [==============================] - 6s 95us/step - loss: 0.2151 - acc: 0.9342 - val_loss: 0.0499 - val_acc: 0.9896
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
60000/60000 [==============================] - 6s 96us/step - loss: 0.1871 - acc: 0.9402 - val_loss: 0.0388 - val_acc: 0.9897
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
60000/60000 [==============================] - 6s 97us/step - loss: 0.1675 - acc: 0.9446 - val_loss: 0.0418 - val_acc: 0.9893
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
60000/60000 [==============================] - 6s 95us/step - loss: 0.1540 - acc: 0.9487 - val_loss: 0.0379 - val_acc: 0.9891
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
60000/60000 [==============================] - 6s 97us/step - loss: 0.1451 - acc: 0.9501 - val_loss: 0.0332 - val_acc: 0.9914
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
60000/60000 [==============================] - 6s 97us/step - loss: 0.1362 - acc: 0.9523 - val_loss: 0.0331 - val_acc: 0.9908
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
60000/60000 [==============================] - 6s 97us/step - loss: 0.1322 - acc: 0.9514 - val_loss: 0.0284 - val_acc: 0.9922
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
60000/60000 [==============================] - 6s 99us/step - loss: 0.1281 - acc: 0.9508 - val_loss: 0.0368 - val_acc: 0.9900
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
60000/60000 [==============================] - 6s 101us/step - loss: 0.1238 - acc: 0.9519 - val_loss: 0.0299 - val_acc: 0.9920
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
60000/60000 [==============================] - 6s 99us/step - loss: 0.1215 - acc: 0.9524 - val_loss: 0.0357 - val_acc: 0.9906
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
60000/60000 [==============================] - 6s 97us/step - loss: 0.1188 - acc: 0.9528 - val_loss: 0.0332 - val_acc: 0.9901
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
60000/60000 [==============================] - 6s 96us/step - loss: 0.1125 - acc: 0.9538 - val_loss: 0.0274 - val_acc: 0.9913
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
60000/60000 [==============================] - 6s 97us/step - loss: 0.1141 - acc: 0.9536 - val_loss: 0.0247 - val_acc: 0.9927
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
60000/60000 [==============================] - 6s 97us/step - loss: 0.1118 - acc: 0.9539 - val_loss: 0.0264 - val_acc: 0.9921
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
60000/60000 [==============================] - 6s 98us/step - loss: 0.1119 - acc: 0.9531 - val_loss: 0.0234 - val_acc: 0.9927
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
60000/60000 [==============================] - 6s 97us/step - loss: 0.1086 - acc: 0.9541 - val_loss: 0.0239 - val_acc: 0.9924
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
60000/60000 [==============================] - 6s 98us/step - loss: 0.1094 - acc: 0.9543 - val_loss: 0.0221 - val_acc: 0.9929
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
60000/60000 [==============================] - 6s 100us/step - loss: 0.1048 - acc: 0.9552 - val_loss: 0.0202 - val_acc: 0.9945
<keras.callbacks.History at 0x7f5b32e47940>


* Evaluate Output

[0.02019497956512496, 0.9945]

* Strategy

Given that the code from 8th variant was already hitting 99.4+ accuracy my foucs was on to reduce the training parameters.
My main focus was to reduce the filters and that is what I did. The number of trainable parameters reduced to 10.5K.
