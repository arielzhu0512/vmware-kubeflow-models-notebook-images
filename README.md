# VMware Kubeflow Models Notebook Images

| Image                                                                               | Description                                       |
| ----------------------------------------------------------------------------------- | ------------------------------------------------- |
| [HuggingFace Hub model inferencing and serving](./hf-inference-deploy/Dockerfile)   | Ready to run and serve models in HuggingFace Hub. |
| [Serve models using Torchserve with GPU](./serve-torchserve-gpu/Dockerfile)         | General image to serve big models using Torchserve server with GPU. |
| [YOLOv5 (helmet) model deployment, fine-tune, KServe](./yolov5/Dockerfile)          | Deploy, fine-tune, and serve YOLOv5 (helmet detection) using KServe. |
| [HuggingFace Hub model with `wget` and `curl`](./hf-inference-serve-wget/Dockerfile) | Ready to run and serve models in HuggingFace Hub, along with extra `wget` and `curl` packages. |