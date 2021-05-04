# Stain-Virtualization
VIRTUALIZATION OF TISSUE STAINING IN DIGITAL PATHOLOGY USING ANUNSUPERVISED DEEP LEARNING APPROACH.
Histopathological evaluation of tissue samples is a key practice in patient diagnosis. Historically, Hematoxylin and Eosin (H&E) has been used by pathologists as a gold standard staining. However, in many cases, various target specific stains, including immunohistochemistry (IHC), are needed in order to highlight specific structures in the tissue. As tissue is scarce and staining procedures are tedious, it would be beneficial to generate images of stained tissue virtually. Virtual staining could also generate in-silico multiplexing of different stains on the same tissue segment. We present a sample application that generates virtual IHC images from real IHC images  and vice versa using an unsupervised deep learning approach based on CycleGAN. 


![image](https://user-images.githubusercontent.com/69753319/117068001-91e01b80-acdf-11eb-8ae5-4bdb94547f0b.png)

DATA PREPARATION :

The "A" category refers to H&E slide and "B" category refers to IHC slide image, and the dataset is comprised of train and test elements. We will load all photographs and use them as a training dataset. First loads all images into memory, showing that there are X images in category A (H&E slide) and Y images in category B (IHC slide). The arrays are then saved in compressed numpy format with the filename "stain.npz". 

GAN Architecture explaination - https://sunilsyengg-100.medium.com/everything-about-gan-e04c296fa69d

Formulation of Objective function in CyclGAN: 

Loss(G,F,D1(H&E),D2(IHC)) = Loss(GAN1)(G,D1,H&E,IHC) + Loss(GAN2)(G,D2,IHC,H&E) + Loss(CYC1)(G,F) + Loss(CYC2)(F,G)
Optimization


G*,F*  = argmin(G,F) argmax(D1,D2) loss(G,F,D1,D2)
