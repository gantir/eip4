
- Did range test and arrived at a learning max_lr: 0.01 and base_lr: 0.001
- Used these as base rates to implement a cyclic LR
- Tried using OCP but was running into errors. So will try it later
- Used image augmentation. Haven't used cutout
- Used the ResNet50V2
- Output (ver 1)
```js
{'gender_output_loss': 0.6895700943085455, 'image_quality_output_loss': 0.9690411398487706, 'age_output_loss': 1.4340560282430341, 'weight_output_loss': 0.9800238436268222, 'bag_output_loss': 0.9187365001247775, 'footwear_output_loss': 1.0454382646468379, 'pose_output_loss': 0.9272902550235871, 'emotion_output_loss': 0.9219263618992221}
{'gender_output_acc': 0.5509072580645161, 'image_quality_output_acc': 0.5660282258064516, 'age_output_acc': 0.3865927419354839, 'weight_output_acc': 0.6446572580645161, 'bag_output_acc': 0.5529233870967742, 'footwear_output_acc': 0.4319556451612903, 'pose_output_acc': 0.6194556451612904, 'emotion_output_acc': 0.7061491935483871}
```
- Output (ver 2)
```js
{'gender_output_loss': 0.6856895505435883, 'image_quality_output_loss': 0.959383507569631, 'age_output_loss': 1.435771276080419, 'weight_output_loss': 0.9941820388748532, 'bag_output_loss': 0.901576438593486, 'footwear_output_loss': 1.0300683795459686, 'pose_output_loss': 0.9425125869493636, 'emotion_output_loss': 0.899781620691693}
{'gender_output_acc': 0.5610119047619048, 'image_quality_output_acc': 0.5793650793650794, 'age_output_acc': 0.40625, 'weight_output_acc': 0.6235119047619048, 'bag_output_acc': 0.5768849206349206, 'footwear_output_acc': 0.4568452380952381, 'pose_output_acc': 0.6021825396825397, 'emotion_output_acc': 0.7162698412698413}
```


Reference:
- https://github.com/titu1994/keras-one-cycle
- https://github.com/bckenstler/CLR
