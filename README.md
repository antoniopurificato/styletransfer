# styletransfer
 
This project was developed for the **Vision And Perception** exam, academic year 2021/2022, University La Sapienza of Rome.
 
## Getting Started
 
The aim of this project is to perform Style Transfer with 2 different approaches. <br>The first one is based on Neural Style Transfer while the second one is based on Generative Adversarial Networks (GANs). <br>For this task the idea is to modify faces images and panoramas with Van Gogh pictures.
 
### GAN Style Transfer
There are 2 datasets for this task. The first one is a web scraped set of human faces of different ages,races and creeds downloaded from [Kaggle](https://www.kaggle.com/datasets/ashwingupta3012/human-faces). The second one is a set of Van Gogh Paintings collected from the [Berkeley](https://people.eecs.berkeley.edu/%7Etaesung_park/CycleGAN/datasets/) university. <br> For this task is used CycleGAN. We adopt the architecture for our generative networks  who have shown impressive results. It is possible to see that there are 2 generators and 2 discriminators because we have 2 different domains and it is not possible in this case to use one single couple generator-discriminator. <br> The incredible thing is that the same network was used also for Panoramas' Style Transfer with good results. Also in  this case the set of panoramas was downloaded from [Berkeley](https://people.eecs.berkeley.edu/%7Etaesung_park/CycleGAN/datasets/).
 
### Neural Style Transfer
This approach was inspired by the works [2] and [3]. The model was trained on the human faces dataset, used also on the other task. Only one style image was used. To learn the content of the image to transform the algorithm minimizes the difference of features extracted at various depths of a pretrained VGG16 model, between said image and the produced one. To learn the style of the reference image instead, the model minimizes the norm of the difference between Gram matrices created from features extracted again from layers at various depths of the same VGG16 model. Since the model had trouble learning to color correctly the produced images a second model was developed that worked with gray images. Color is later added from the original by converting the images from RGB to the LAB color space.
 
## Installing 
 
In this repository there are 5 Colab Notebooks. All the code can be runned using Google Drive on every browser.<br>
You have simply to paste all the Notebooks in your Drive.<br>
The main notebook is *MainNotebook*. In this notebook is possible to find a setup cell. This cell must be runned only the first time and then must be commented. Using this cell is possible to download all the datasets that are required. In this way is not necessary to download the datasets by hand but all is done automatically. With this setup also some pretrained models are downloaded and in this way is possible to use them only for testing and to see the results.<br>
Is also possible to use the other 4 Notebooks for training but but is descouraged because the execution time is about 4 hours of GPU for every Notebook to achieve results close to our pretrained models.
 
## Results
 
### GAN Style Transfer
Is possible to see the results in two ways. In the first one we run the TrainingNotebookFaces or TrainingNotebookPanoramas (depending on the task) and we wait to train our network, if for instance we want to change something. But we can also open *MainNotebook* and use the pretrained models provided by us. Is possible to see how the loss decreases over time and we can see the modified pictures both for the panoramas and for the human faces.
<p align="center">
 <img src="/src/faces.png" width="500" title="Network result on faces" >
<p\>
	<p align="center">
 <img src="/src/panoramas.png" width="500" title="Network result on panoramas" >
<p\>
 
### Neural Style Transfer
The model can be trained as shown in TrainingNotebookNeural and TrainingNotebookNeuralGray. Pretrained models are also  available and *MainNotebook* shows how to use them. The advantage of the approach from [3] as opposed to [2] is that the model, during inference, can be called as any other model and it does not need to be trained every time a new image is produced.
<p align="center">
 <img src="/src/original.png" width="500" title="Original images" >
<p\>
<p align="center">
 <img src="/src/color.png" width="500" title="Network learning colors." >
<p\>
<p align="center">
 <img src="/src/gray.png" width="500" title="Network working in grayscale with colors added after." >
<p\>


## Authors
- *[Antonio Purificato](https://github.com/antoniopurificato)* - Style Transfer using Generative Adversarial Networks 
 
- *[Marco Montagna](https://github.com/Coerulatus)* - Neural Style Transfer

- *[Leonardo Mongelli](https://github.com/Leonardo9900)* - Neural Style Transfer and Style Transfer using Generative Adversarial Networks
 
## References
 
### Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks
```
@inproceedings{CycleGAN2017,
 title={Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks},
	
 author={Zhu, Jun-Yan and Park, Taesung and Isola, Phillip and Efros, Alexei A},
	
 booktitle={Computer Vision (ICCV), 2017 IEEE International Conference on},
	
 year={2017}
}
```


### A Neural Algorithm of Artistic Style
```
@misc{https://doi.org/10.48550/arxiv.1508.06576,
  doi = {10.48550/ARXIV.1508.06576},
 
  url = {https://arxiv.org/abs/1508.06576},
 
  author = {Gatys, Leon A. and Ecker, Alexander S. and Bethge, Matthias},
  
  title = {A Neural Algorithm of Artistic Style},
 
  publisher = {arXiv},
 
  year = {2015},
 
  copyright = {arXiv.org perpetual, non-exclusive license}
}
```

### Perceptual Losses for Real-Time Style Transfer and Super-Resolution
```
@misc{https://doi.org/10.48550/arxiv.1603.08155,
  doi = {10.48550/ARXIV.1603.08155},
 
  url = {https://arxiv.org/abs/1603.08155},
 
  author = {Johnson, Justin and Alahi, Alexandre and Fei-Fei, Li},
 
  title = {Perceptual Losses for Real-Time Style Transfer and Super-Resolution},
 
  publisher = {arXiv},
 
  year = {2016},
 
  copyright = {arXiv.org perpetual, non-exclusive license}
}
```
