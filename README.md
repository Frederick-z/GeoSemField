# GeoSemField
# Dataset
## Data preparation

All datasets can be obtained by following the official instructions or download links provided by the corresponding baseline projects:
- **LERF-OVS**: please follow the dataset preparation instructions in [LangSplat](https://github.com/minghanqin/LangSplat)
- **3D-OVS**: please follow the official release in [3D-OVS](https://github.com/kunhao-liu/3d-ovs)
- **MipNeRF360v2**: please download the data from the official [Mip-NeRF 360 page](https://jonbarron.info/mipnerf360/)

# Train
## Directory Layout

```text
standard_code/
├── configs/fusion_mainline.yaml
├── fusion/
│   ├── run_fusion_training.py
└── geosemfield/
    ├── arguments/
    ├── gaussian_renderer/
    ├── scene/
    ├── utils/
    ├── geosemfield/
    ├── tools/
    ├── ext/
    └── submodules/
```

## Environment

Create the environment from `environment.yml`, then build the local CUDA
extensions:

```bash
conda env create -f environment.yml
conda activate goi
cd geosemfield/submodules/diff-gaussian-rasterization
pip install -e .
cd ../simple-knn
pip install -e .
cd ../../..
```
