# GeoSemField
While 3D semantic Gaussian splatting pipelines establish scene-level semantic associations, they inherently fail to translate this continuous relevance into precise target-extent prediction. Existing language-conditioned pipelines typically render a semantic feature map and derive predictions through post-hoc similarity comparisons with a text query. While these methods effectively highlight semantically relevant neighborhoods, they fail to definitively assign rendered pixels or Gaussians to a queried target when objects are adjacent, nested, or frequently co-occurring. We investigate this critical gap between semantic relevance and true target membership, proposing \textbf{GeoSemField}, a geometry-aware and language-conditioned semantic field tailored for explicit target-extent prediction in 3DGS. Our framework extracts viewpoint-aligned semantic carriers from a shared 3DGS representation and optimizes a query-conditioned target field over this rendered evidence. By incorporating feature-space Eikonal regularization alongside geometry-alignment constraints, our method strictly regulates response transitions. This formulation ensures that continuous semantic relevance is reliably converted into stable, discrete target boundaries. Extensive experiments on open-vocabulary 3D segmentation and localization benchmarks, supported by comprehensive ablations and leakage diagnostics, demonstrate that explicit target-membership estimation significantly enhances object isolation and mitigates semantic leakage in cluttered environments compared to existing methods.


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
