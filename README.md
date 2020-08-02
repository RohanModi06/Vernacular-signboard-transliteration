# Vernacular-signboard-transliteration

In this project, we have built models for text detection, text recognition and transliteration from hindi to english. It is implemented using PyTorch. Transliteration is the phonetic translation of the words in a source language ( here hindi ) into equivalent words in a target language ( here english ). 


### Dataset: 

Text detection:                                                                                
train data - https://drive.google.com/file/d/1E5kI8CLoC-XffqQMTWwSpBIPp1Wb2tne/view?usp=sharing       
test data - https://drive.google.com/file/d/1C0-mc0WAIdssS5KJwOjghaWaqiImZZUr/view?usp=sharing    

Text recognition:                                                                               
train data - https://drive.google.com/file/d/1E5kI8CLoC-XffqQMTWwSpBIPp1Wb2tne/view?usp=sharing     
test data - https://drive.google.com/open?id=1C0-mc0WAIdssS5KJwOjghaWaqiImZZUrg     

Transliteration:     
train data - https://drive.google.com/file/d/1eha4iSfIK41Im9Kacd32l3c0ZxxJjClX/view?usp=sharing       
test data - https://drive.google.com/file/d/1h1bnxUksOgasexvz3IFdIWZbwPPklIOq/view?usp=sharing    


### Overall architecture of model:

Text detection:
Facebook detectron2 R50-FPN Mask R-CNN pretrained model is being fine tuned with our dataset. The evaluation is being done using the AP metric.  

Text recognition:  
The annotations recieved from the text detection is used to crop and resize the images to input size.   
The crnn model is being used with its first layer as the pretrained resnet18 followed by 2-layer CNN consisting of Conv-2d and BatchNorm and at last followed by the GRUs.  
CTC is being used as the loss function, with Adam as the optimizer and Xavier initialization.  

Transliteration:  
Dictionaries of character are made corresponding to character id and vice versa for both the source and target characters (vocabulary).   
Each character in the list of words is converted to the corresponding index with the help of look-up tables.  
The general EncoderDecoder model with Attention is being implemented using GRU. Optimizer is Adam and Xavier initialization is used.  
Loss used is Log loss and accuracy metric is used for evaluation.  

### Trained models:  
Text detection: https://drive.google.com/drive/folders/1Y-tPfhlCvCcuDQ6CvabNgdEkV-GEbE-a?usp=sharing  
Text recognition: https://drive.google.com/file/d/1KUrprUKJqs6tEEqHObQ6s7QkYXEymxKA/view?usp=sharing  
Transliteration: https://drive.google.com/file/d/1bNh5PwU0h_91EviU3Csq2GtOrQExZKZg/view?usp=sharing  
