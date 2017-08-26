## Polyvore Dataset
Dataset used in ACM MM'17 paper "Learning Fashion Compatibility with Bidirectional LSTMs" [[paper]](https://arxiv.org/pdf/1707.05691.pdf).

### Contact
Author: Xintong Han

Contact: xintong@umd.edu

### Polyvore.com

[Polyvore.com](https://www.polyvore.com/outfits/search.sets?date=day&item_count.from=4&item_count.to=10) is a popular fashion website, where user can create and upload outfit data. Here is an [exmaple](https://www.polyvore.com/striped_blazer/set?id=227166819).

### Dataset

Download and decompress polyvore.tar.gz.

#### Polyvore outfits

This dataset contains 21,889 outfits from polyvore.com, in which 17,316 are for training, 1,497 for validation and 3,076 for testing. The train, validation and test outfits are in {train,valid,test}_no_dup.json, respectively.

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
    

If you do not want to download all these images using their urls, you can download them via [Google Drive](https://drive.google.com/drive/folders/0B4Eo9mft9jwoVDNEWlhEbUNUSE0). This file contains the images of 33,375 outfits, which include all 21,889 outfits in polyvore dataset. The other ~11k outfits are uploaded more than 3 years ago. We are afraid that they are out-of-fashion so we do not use them).

#### Fill-in-the-blank Fashion Recommendation

fill_in_the_blank_test.json contains the questions used to evaluate in the fill-in-the-blank fashion recommendation task. It follows the following format:

    {
        "question": Fashion item sequence to form the question,
        "answers": Multiple choice set to choose from,
        "blank_position": The blank position to be filled in.
    },
    
The name of a fashion item is SetID_ItemIndex, _e.g._, 119704139_1 is the fashion item with "index" 1 in the outfit with "set_id" 119704139.


#### Fashion Compatibility Prediction

fashion-compatibility-prediction.txt contains ~7,000 outfits, where 4,000 are incompatible and 3,000 are compatible.

In each line the first number indicating the compatibility (1 is compatible, 0 is not) followed by a sequence of fashion items consisting the outfit.

### Some Notes
0. These outfits are crawled around 02/19/2017, so you can estimate the extact upload date of an outfit by looking at the "date" filed.

0. For outfits that contain too many fashion items, we only keep their first 8 items.

0. We delete the fashion items with non-fashion "categoryid" such as background, texts, decorations. As a result, the indices of items in an outfit may not be consecutive.


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

1. Mining Fashion Outfit Composition Using An End-to-End Deep Learning Approach on Set Data. [[paper]](https://arxiv.org/pdf/1608.03016.pdf) [[dataset]](https://github.com/raingo/outfit)
