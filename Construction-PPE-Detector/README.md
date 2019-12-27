# PPE Detector for Worker Safety
[The PPE Detector for Worker Safety](https://aws.amazon.com/marketplace/pp/prodview-6gvzwuebead3o) - is a real-time computer vision model for PPE non-compliance detection in the industrial setting. The solution detects seven object classes: Bare Head, Helmet, Ear Protection, Welding Mask, Bare Chest(NO Visibility Vest), High Visibility Vest, Person.

[![AWS Marketplace](AWS-Marketplace.png)](https://aws.amazon.com/marketplace/pp/prodview-6gvzwuebead3o)

## Usage Information

Using our model for real time prediction is as simple as this:

```python
predictor = sagemaker.predictor.RealTimePredictor(
    ' your endpoint name ',
    sagemaker_session=sagemaker.Session(),
    content_type="image/jpeg"
)

with open('data/sample_image.jpg', 'rb') as img:
    img_bytes = bytearray(img.read())
    result = predictor.predict(img_bytes).decode("utf-8")
```

Also we've published two notebooks showing how to use our model:
* [Using-PPE-Detector-Endpoint.ipynb](Using-PPE-Detector-Endpoint.ipynb) notebook shows how you can use Python API to perform inference on endpoint created from the model
* [Using-Personal-Protection-Equipment-Detection-model.ipynb](Using-Personal-Protection-Equipment-Detection-model.ipynb) notebook shows how you can use Python API to run the full scenario:
    * deploy our model to create an endpoint
    * run Real Time inference on endpoint using local image
    * visualize  and save the prediction on original image
    * run Batch Transform job to perfom the inference on your data stored in Amazon S3 bucket

## Input\output data examples

* You can find sample input data in [demo_input](data/test_samples/demo_input) folder
* [demo_output_images](data/test_samples/demo_output_images) folder contains images with detections predicted by the model and visualized using `utils.visualize_detection` method
* [demo_raw_output](data/test_samples/demo_raw_output) folder contains raw output generated by our model using `Batch Transform` approach

## Sample detection results:

![PPE Detector output example](data/test_samples/demo_output_images/54_11.Welder_in_Egypt_%28...jpg?raw=true)

![PPE Detector output example](data/test_samples/demo_output_images/17_34.160728-F-VV898-05...jpg?raw=true)

![PPE Detector output example](data/test_samples/demo_output_images/79_32.site-1536859_960_...jpg?raw=true)

![PPE Detector output example](data/test_samples/demo_output_images/108_87.13520761816095.jp...jpg?raw=true)