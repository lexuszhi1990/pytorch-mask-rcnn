### setup docker env

docker run --network host --ipc host -v /home/david/fashionAI/pytorch-mask-rcnn:/app -v /data/david/cocoapi:/mnt/dataset/coco -v /data/david/models/pytorch-mask-rcnn:/mnt/ckpt/pytorch-mask-rcnn -it --rm floydhub/pytorch:0.3.0-gpu.cuda9cudnn7-py3.22-dev bash

### build packages

```
cd nms/src
nvcc -c -o nms_kernel.cu.o nms_kernel.cu -x cu -Xcompiler -fPIC -arch=sm_61
cd ../../
python build.py
cd ../../

cd roialign/roi_align/src/cuda/
nvcc -c -o crop_and_resize_kernel.cu.o crop_and_resize_kernel.cu -x cu -Xcompiler -fPIC -arch=sm_61
cd ../../
python build.py
cd ../../
```
