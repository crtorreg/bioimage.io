
# Tutorial for contributing models
**Note: only PyTorch and TensorFlow models are supported at the moment. We are working on alternative model formats such as ONNX.**

For contributing models, it is needed to (1) generate the model, (2) upload the model to Zenodo, (3) wait for the Bioimage Model Zoo approval and respond to the potential issues that can appear. All these steps are explained below.

<p align="center">
<img src="https://github.com/crtorreg/bioimage.io/blob/crtorreg-patch-1/docs/contribute_models/contribute_model.png" align="center" width="1000"/>
</p>

## Model generation
 
1. Generate your model and check (1) that it is supported by the BioImage Model Zoo and (2) it is compatible with at least one of the consumer software. Check it [here](https://github.com/bioimage-io/spec-bioimage-io/blob/master/supported_formats_and_operations.md). There are two ways to generate this model depending on the user type. 
   - For most users, the model package can be generated from compatible software tools (e.g. zerocost notebooks, Fiji plugin etc.)
   - For developers, the model package can be generated manually via the bioimageio.core package [(e.g. Function to build the model)](https://github.com/bioimage-io/core-bioimage-io-python/blob/902262bdce60a4c905f7b4a3b5646dc9ae68122f/bioimageio/core/build_spec/build_model.py#L572-L589).

2. The model specification should fulfill the following criteria [BioImage.IO Model Resource Description File Specification](https://github.com/bioimage-io/spec-bioimage-io/blob/gh-pages/model_spec_latest.md). 
   - Each field on the file can be either mandatory or optional. You can use [our template](https://github.com/bioimage-io/bioimage-io-models/pull/55/files#diff-f6c64be5b9d764d0964654908b2ed4495fccc7624e58e9360bfdc6cef169edbe) to fill in the required information. 
   - [Here is an example](https://github.com/bioimage-io/pytorch-bioimage-io/blob/master/specs/models/unet2d_nuclei_broad/UNet2DNucleiBroad.model.yaml) of a filled configuration YAML file. On the Bioimage Model Zoo web page you will also find different examples. 

3. It is recommended before uploading the model into zenodo to ensure locally that your model is compatible with the latest [Bioimage.io model format](https://github.com/bioimage-io/spec-bioimage-io/blob/gh-pages/model_spec_latest.md). To do that a python package called ´bioimageio.core´ has been created, all the steps to validate and test your model are available in the following [documentation](https://github.com/bioimage-io/spec-bioimage-io#bioimageio-cli). More specifically, with `test-model` you will check the validity of your model specification file and later, with `validation-model` you will prove that your model runs properly. 


## Upload to Zenodo repository
4. Once your model is ready, we can start uploading the model to the [bioimage.io website](https://bioimage.io/#/). You should go to the [bioimage.io website](https://bioimage.io/#/) and click on `+Upload`, then follow the steps:

   - Log in to Zenodo and give access to the BioEngine Application through email verification. You will see an automatic message once you are logged in. If not, refresh the page.
   This step needs to be done just for the first time you upload a model. 
   - Upload the model RDF specification file.
   
   <p align="center">
   <img src="https://github.com/crtorreg/bioimage.io/blob/main/docs/contribute_models/upload_1.png" align="center" width="500"/>
   </p>
   
   - Complete the missing fields. Check out how to get most of your model documentation.
    
   <p align="center">
   <src="https://github.com/crtorreg/bioimage.io/blob/main/docs/contribute_models/upload_2.png" align="center" width="500"/>
   <img src="https://github.com/crtorreg/bioimage.io/blob/main/docs/contribute_models/upload_3.png" align="center" width="500"/>
   </p>
   
   - Validate your model. It is needed to click on the **validate button** to verify the model compatibility with the Bioimage.io specifications. Once the validation has been successful, you can load your model into the [bioimage.io website](https://bioimage.io/#/). 
   <p align="center">
   <img src="https://github.com/crtorreg/bioimage.io/blob/crtorreg-patch-1/docs/contribute_models/upload_4.png" align="center" width="500"/>
   </p>

## Model approval

5. Once your model has been uploaded successfully into the Zenodo repository a pull request is gonna be created in the [bioimage-io collection repository](https://github.com/bioimage-io/collection-bioimage-io/pulls). During this PR the model must pass several checks in the CI repo to be accepted, once pass all these steps a member of the Bioimage Model Zoo team would accept the model to be visible through the [website](https://bioimage.io/#/). 

6. It is important to note that after the model gets accepted, you can make corrections by clicking the pencil/edit button on the model card to edit meta information, create a new version etc. If a new version is detected, it will trigger the CI under the collection repo, and repeat the approval process for the new version(s).

# How to get most of your model documentation
## Model Tags

The tags in the model RDF are used to search for each model in the BioImage Model Zoo. The more informative tags you write, the easier it will be for a potential user to find your model. Example:

**My model description**: An encoder-decoder trained for denoising of point-scanning super-resolution microsocpy images of HeLa cells microtubules

**Tags**: `denoising`, `PSSR`, `microtubules`, `encoder-decoder`, `deblurring`, `fluorescence`, `2D`, `HeLa cells`, `deepimagej`, `ilastik`, `image restoration`, `trained-model` etc.

## Considerations for the model description file (format_version>=0.4.2)
When following the [BioImage.IO Model Resource Description File Specification](https://github.com/bioimage-io/spec-bioimage-io), it is important that you pay special attention to the following:
* Choose an input and output test images so we can check that your model runs correctly in the chosen [consumer software](https://bioimage.io/docs/#/consumer_software/model_runner)
* Choose a representative cover image of the task performed by your model. This image will be used in the model card to guide the users through the model search.
* Pre-processing and post-processing should be always described. For that, you can check which [processing routines are supported](https://github.com/bioimage-io/spec-bioimage-io/blob/master/supported_formats_and_operations.md#pre--and-postprocessing) at the moment. 
* Do not forget to include in your bioimage model (.zip) any additional file needed for the correct execution of the model.

