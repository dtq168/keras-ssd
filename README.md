# Preface

This is the copy of [this](https://github.com/rykov8/ssd_keras) repository.

# Setup environment

```
$ conda env create -f environments.yml
```

The command will install below libs

This code was tested with `Keras` v2.0.0, `Tensorflow` v1.0.0, `OpenCV` v3.2.0.6

# Create meta file for training from VOC format

- Modify categories in `_to_one_hot` in `get_data_from_XML.py`
- Add below code at the end of the `get_data_from_XML.py`

```
import pickle
data = XML_preprocessor('<PATH_TO_ANNOTATIONS>').data
pickle.dump(data,open('<FILE_NAME>.pkl', 'wb'))
```

- Change `NUM_CLASSES` to be actual number of classes + 1 auxiliary background class. (refer [this](https://github.com/rykov8/ssd_keras/issues/17) discussion)

- Make sure batch size is small enough otherwise infinite loop will be happen for data generation

# AWS GPU Usage

Run jupyter

```
$ source activate aind2
$ jupyter notebook --ip=0.0.0.0 --no-browser
```