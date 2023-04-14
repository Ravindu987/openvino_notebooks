# Convert and Optimize Typo Detector with OpenVINO™

Typo detection in AI is a process of identifying and correcting typographical errors in text data using machine learning algorithms. The goal of typo detection is to improve the accuracy, readability, and usability of text by identifying and correcting mistakes made during the writing process.

A typo detector takes a sentence as an input and identify all typographical errors such as misspellings and homophone errors.

This tutorial provides how to use the [Typo Detector](https://huggingface.co/m3hrdadfi/typo-detector-distilbert-en) from the [Hugging Face Transformers](https://huggingface.co/docs/transformers/index) library to perform the above task.

The model has been pretrained on the [NeuSpell](https://github.com/neuspell/neuspell) dataset.

<img src=https://user-images.githubusercontent.com/80534358/224564463-ee686386-f846-4b2b-91af-7163586014b7.png>

</br>

The notebook provides two methods to use the typo detector in the OpenVino runtime. I've demonstrated both methods so that you can experience both the loading of compiled models and loading models in other frameworks and converting them.

1. Use the [Hugging Face Optimum](https://huggingface.co/docs/optimum/index) library to load the compiled model in OpenVino IR format. Then create a pipeline with the loaded model to run inference.

2. Load the model and convert to ONNX and then to OpenVino IR.
   First the Pytorch model is convereted to the ONNX format and then the [Model Optimizer](https://docs.openvino.ai/latest/openvino_docs_MO_DG_Deep_Learning_Model_Optimizer_DevGuide.html) tool is used to convert to [Openvino IR format](https://docs.openvino.ai/latest/openvino_ir.html). This method provides much more insight to the openvino environment and applications.

The following table summarises the major differences between the two methods

</br>

| Method 1                                                            | Method 2                                                           |
| ------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Load models from Optimum, an extension of transformers              | Load model from transformers                                       |
| Load the model in OpenVino IR format on the fly                     | Have to load the model and convert to ONNX and then to OpenVino IR |
| Load the compiled model by default                                  | Model has to be compiled after converting to OpenVino IR           |
| In this application, loaded model from optimum is around 15% faster | The converted model is slower                                      |
| Pipeline is created to run inference with OpenVINO Runtime          | Have to manually run inference.                                    |

</br>

## Notebook Contents

This tutorial demonstrates step-by-step instructions on how to run and optimize the model.

The tutorial consists of the following steps:

- Required libraries
- Two possible methods
  - Using the HuggingFace Optimum library
    - Loading the compiled model in OpenVino IR format
    - Creating the pipeline
    - Run inference/Demo
  - Using the pipeline to use the model
    - Conversion to ONNX format
    - Conversion to OpenVINO IR format
    - Required helper functions
    - Run inference/Demo

</br>

## Installation Instructions

If you have not installed all required dependencies, follow the [Installation Guide](../../README.md).