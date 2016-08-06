# xtorch-dataset
xtorch dataset module, including `plaindataset`, `listdataset`, which provides a unified interface for training.  

## `plaindataset`
Wraps `X_train`, `Y_train`, `X_test`, `Y_test`. Suitable for small dataset that can be loaded in memory at once.  

```lua
dofile('plaindataset.lua')
ds = PlainDataset({
    X_train = X_train,
    Y_train = Y_train,
    X_test = X_test,
    Y_test = Y_test
})
```

## `listdataset`
Loads images from disk dynamically with a multithread data loader. Suitable for big dataset that cannot fit in memory.  
```lua
dofile('listdataset.lua')
ds = ListDataset({
    trainData = '/search/ssd/liukuang/cifar10/train/',
    trainList = '/search/ssd/liukuang/cifar10/train.txt',
    testData = '/search/ssd/liukuang/cifar10/test/',
    testList = '/search/ssd/liukuang/cifar10/test.txt',
    imsize = 32
})
```

|-- trainData  
|-- testData  
|-- trainList  
|-- testList  

- `trainData`&`testData` are folders containing training/test images.  
- `trainList`&`testList` are txt files containing the image names & labels/targets separated by spaces.
