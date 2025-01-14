# Contribute Models

## Model contribution requirements:

- Follow the [BioImage.IO Model Resource Description File Specification](https://github.com/bioimage-io/spec-bioimage-io/blob/gh-pages/model_spec_latest.md) with `format_version>= 0.4.2`.
- Any contributed model should run on at least one [consumer software](https://github.com/bioimage-io/spec-bioimage-io/blob/master/supported_formats_and_operations.md#consumers).
- **Special case**: Notebook contribution together with an example model.

## Tutorial

 <img src="https://github.com/crtorreg/bioimage.io/blob/main/docs/contribute_models/contribute_model.png" align="center" width="1000"/>

Model contribution means that you will upload a fully-documented trained model to a public repository using the Upload Buttom from [Bioimage Model  Zoo](https://bioimage.io/#/). Uploading your model to the Bioimage Model Zoo ensures that:
- The model is well documented.
- It can be used by biologists through user-friendly tools. 
- It is assigned a unique DOI identifier and a License.
- The model is public and can be used by anyone under the chiosen licensing conditions.

The model package contains the trained weights together with the architecture, example inputs and outputs, and the configuration specification file that describes your model technically in such a way that at least one of the consumer software can load and run the model. All this information is embedded in a specific file called [`Model Resource Description File` (RDF)](https://github.com/bioimage-io/spec-bioimage-io/blob/gh-pages/model_spec_latest.md). 

Once the model is uploaded to Zenodo, it will be created a pull request in [bioimage-io/collection-bioimage-io repository](https://github.com/bioimage-io/collection-bioimage-io/pulls). It will be assessed by a Continuos Integration (CI) workflow to check for its usability in at least one of the consumer software. When the pull request is created, you must take care to check whether the new item or version passes the different requirements. Once it passes, it should be approved by at least one of the BioImage.IO admin team member and later it will be displayed in the BioImage Model Zoo. 

Ready to follow the [Tutorial](/contribute_models/tutorials.md)?

## Contributing other resource types

To contribute a notebook, application or dataset, please use the generic [Resource Description File Format](https://github.com/bioimage-io/spec-bioimage-io/blob/main/README.md).
