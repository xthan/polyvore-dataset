## Polyvore Dataset
Dataset used in ACM MM'17 paper "Learning Fashion Compatibility with Bidirectional LSTMs" [[paper]](https://arxiv.org/pdf/1707.05691.pdf) [[code]](https://github.com/xthan/polyvore)

This dataset is also available on [Google Drive](https://drive.google.com/drive/folders/0B4Eo9mft9jwoVDNEWlhEbUNUSE0?resourcekey=0-vQg9TMSLKnmPCuuWwl5Ebw&usp=sharing).
Original Images can be downloaded on [Kaggle]( https://www.kaggle.com/datasets/dnepozitek/maryland-polyvore-images/data).

**A clean version of this dataset can be found:** [**Cleaned Maryland**](https://github.com/AemikaChow/AiDLab-fAshIon-Data/blob/main/Datasets/cleaned-maryland.md)

You may be interested in a new dataset [A100 dataset](https://github.com/AemikaChow/AiDLab-fAshIon-Data/blob/main/Datasets/A100.md), which measures the aesthetic ability of an AI model.

### Contact
Author: Xintong Han

Contact: xintong@umd.edu

### Polyvore.com

Polyvore.com is a popular fashion website, where users can create and upload outfit data. This website has been acquired by SSense, and the URLs in the dataset are no longer available.

### Dataset

Download and decompress polyvore.tar.gz.

#### Polyvore outfits

This dataset contains 21,889 outfits from polyvore.com, of which 17,316 are for training, 1,497 for validation, and 3,076 for testing. The train, validation, and test outfits are in {train,valid,test}_no_dup.json, respectively.

Each JSON item has the following information:

    {
        "name": Name of the outfit, 
        "views": Number of views of the outfit,
        "items": [
            Fashion items in the outfit.
            {
                "index": Index of the fashion item in this outfit on Polyvore,
                "name": Description of the fashion item,
                "price": Price of the fashion item (usually in US dollars),
                "likes": Number of likes of the item,
                "image": Image url of the item,
                "categoryid": Category ID of the item,
            }, 
            {
                ...
            }, 
            ...
        ], 
        "image": Outfit image url,
        "likes": Number of likes of the outfit,
        "date": Upload date of the outfit,
        "set_url": Outfit url,
        "set_id": Outfit ID,
        "desc": Outfit description.
    }
    

The image URLs are no longer available and they can be accessed on an unofficial [Kaggle page]( https://www.kaggle.com/datasets/dnepozitek/maryland-polyvore-images/data). This file contains the images of 33,375 outfits, which include all 21,889 outfits in polyvore dataset. The other ~11k outfits were uploaded more than 3 years ago. We are afraid that they are out-of-fashion so we do not use them).

[category_id.txt](https://github.com/xthan/polyvore-dataset/blob/master/category_id.txt) contains the mapping between category ID and category name. Thanks [Zhenyu](https://github.com/zyyang) for providing it!

#### Fill-in-the-blank Fashion Recommendation

fill_in_the_blank_test.json contains the questions used to evaluate the fill-in-the-blank fashion recommendation task. It follows the following format:

    {
        "question": Fashion item sequence to form the question,
        "answers": Multiple choice set to choose from,
        "blank_position": The blank position to be filled in.
    },
    
The name of a fashion item is SetID_ItemIndex, _e.g._, 119704139_1 is the fashion item with "index" 1 in the outfit with "set_id" 119704139. The first answer in "answers" is the correct one (_i.e.,_ the original fashion item in the outfit). 


#### Fashion Compatibility Prediction

fashion-compatibility-prediction.txt contains ~7,000 outfits, where 4,000 are incompatible and 3,000 are compatible.

In each line, the first number indicates compatibility (1 is compatible, 0 is not) followed by a sequence of fashion items consisting of the outfit.

### Some Notes
0. These outfits are crawled around 02/19/2017, so you can estimate the exact upload date of an outfit by looking at the "date" field.

0. For outfits that contain too many fashion items, we only keep their first 8 items.

0. We delete the fashion items with non-fashion "categoryid" such as background, texts, and decorations. As a result, the indices of items in an outfit may not be consecutive.


### Citation

If this dataset helps your research, please cite our paper:

    @inproceedings{han2017learning,
      author = {Han, Xintong and Wu, Zuxuan and Jiang, Yu-Gang and Davis, Larry S},
      title = {Learning Fashion Compatibility with Bidirectional LSTMs},
      booktitle = {ACM Multimedia},
      year  = {2017},
    }

### Other Datasets from Polyvore.com

There are several datasets crawled from Polyvore.com:

0. The Elements of Fashion Style. [[paper]](http://ranjithakumar.net/resources/vaccaro-uist2016-fashion.pdf) [[dataset]](https://github.com/kristenvaccaro/fashion-data)

0. Mining Fashion Outfit Composition Using An End-to-End Deep Learning Approach on Set Data. [[paper]](https://arxiv.org/pdf/1608.03016.pdf) [[dataset]](https://github.com/raingo/outfit)

0. NeuroStylist: Neural Compatibility Modeling for Clothing Matching. [[paper]](https://drive.google.com/file/d/0B9ef99fUwsVZbjIxNUlKTFZMWUU/view) [[dataset]](http://neurostylist.farbox.com/)

0. Learning Type-Aware Embeddings for Fashion Compatibility. [[paper]](https://arxiv.org/pdf/1803.09196.pdf)[[dataset]](https://github.com/mvasil/fashion-compatibility)[[cleaned dataset]](https://github.com/AemikaChow/AiDLab-fAshIon-Data/blob/main/Datasets/cleaned-type.md)

0. How Good Is Aesthetic Ability of a Fashion Model? [[paper]](https://openaccess.thecvf.com/content/CVPR2022/papers/Zou_How_Good_Is_Aesthetic_Ability_of_a_Fashion_Model_CVPR_2022_paper.pdf)[[dataset]](https://github.com/AemikaChow/AiDLab-fAshIon-Data/blob/main/Datasets/A100.md)
