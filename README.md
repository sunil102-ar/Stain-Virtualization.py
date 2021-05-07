# Stain-Virtualization
VIRTUALIZATION OF TISSUE STAINING IN DIGITAL PATHOLOGY USING AN UNSUPERVISED DEEP LEARNING APPROACH.

Historically, Hematoxylin and Eosin (H&E) has been used by pathologists as a gold standard staining. However, in many cases, various target specific stains, including immunohistochemistry (IHC), are needed in order to highlight specific structures in the tissue. As tissue is scarce and staining procedures are tedious, it would be beneficial to generate images of stained tissue virtually. Virtual staining, is to use computerized algorithms to create an artiﬁcial eﬀect of staining without physically tampering the slide.We present a sample application that generates virtual IHC images from real H&E images  and vice versa using an unsupervised deep learning approach based on CycleGAN. 

DATA PREPARATION :

The "A" category refers to H&E slide and "B" category refers to IHC slide image, and the dataset is comprised of train and test elements. We will load all photographs and use them as a training dataset. First loads all images into memory, showing that there are X images in category A (H&E slide) and Y images in category B (IHC slide). The arrays are then saved in compressed numpy format with the filename "stain.npz". 

GAN Architecture explaination - https://sunilsyengg-100.medium.com/everything-about-gan-e04c296fa69d

We call one generator G, and have it convert images from the X domain to the Y domain. The other generator is called F, and converts images from Y to X.

![image](https://user-images.githubusercontent.com/69753319/117100103-c11a7b00-ad27-11eb-937c-6422c5cec8a8.png)

Each generator has a corresponding discriminator, which attempts to tell apart its synthesized images from real ones.

![image](https://user-images.githubusercontent.com/69753319/117100181-f45d0a00-ad27-11eb-8d34-5a4a54fb3287.png)

Formulation of Objective function in CyclGAN: 

Adversarial loss:

![image](https://user-images.githubusercontent.com/69753319/117100222-1191d880-ad28-11eb-98c9-05bd03bbebe0.png)

The adversarial loss alone is not sufficient to produce good images, as it leaves the model under-constrained. It enforces that the generated output be of the appropriate domain, but does not enforce that the input and output are recognizably the same. For example, a generator that output an image y that was an excellent example of that domain, but looked nothing like x, would do well by the standard of the adversarial loss, despite not giving us what we really want.

The cycle consistency loss addresses this issue. It relies on the expectation that if you convert an image to the other domain and back again, by successively feeding it through both generators, you should get back something similar to what you put in. It enforces that F(G(x)) ≈ x and G(F(y)) ≈ y.

![image](https://user-images.githubusercontent.com/69753319/117100395-7ea56e00-ad28-11eb-8ad1-6d7147febf31.png)

Complete Objective function :

![image](https://user-images.githubusercontent.com/69753319/117100449-9ed52d00-ad28-11eb-8bb5-f03098ceb01f.png)

Image translation H&E stain image to IHC stain image

![image](https://user-images.githubusercontent.com/69753319/117100658-1f942900-ad29-11eb-8da3-e435880abe8f.png)

IHC stain image to H&E stain image

![image](https://user-images.githubusercontent.com/69753319/117100693-3d618e00-ad29-11eb-86c7-5170cc29222a.png)


