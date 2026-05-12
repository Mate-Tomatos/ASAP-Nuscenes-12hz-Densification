# ASAP nuScenes Trainval Densification

This repository is an unofficial adaptation of the original ASAP codebase for nuScenes annotation densification.

The upstream ASAP project provides the core densification method and original implementation. This repository mainly focuses on adapting the original validation-only densification pipeline to the full nuScenes trainval split and releasing the generated 12Hz densified nuScenes metadata files for research use.

> **Disclaimer:** This repository is not the official ASAP repository. It is an unofficial engineering adaptation based on ASAP. The core method, model design, and original implementation belong to the ASAP authors.

## Relationship to the Original ASAP Project

This project is based on the original ASAP repository:

```text
https://github.com/JeffWang987/ASAP
```

All core ideas, model design, and the original densification pipeline come from the ASAP authors. This repository does not claim ownership of the ASAP method.

My work mainly includes:

1. Adapting the densification pipeline from validation-only processing to full trainval processing.
2. Organizing the modified code for easier reproduction.
3. Releasing the generated 12Hz densified nuScenes `.pkl` metadata files.

If you use this repository, please also refer to and cite the original ASAP project.

## What Is Modified

Compared with the original ASAP implementation, this repository mainly includes the following modifications:

### 1. Trainval Densification Support

The original ASAP pipeline mainly supports densification for the validation split. In this repository, the data processing and generation pipeline has been modified to support both the training and validation splits of nuScenes.

### 2. Released 12Hz Densified nuScenes Metadata

This repository provides generated 12Hz `.pkl` metadata files for the nuScenes trainval split. These files can be used for downstream autonomous driving perception, reconstruction, and temporal modeling experiments.

## Main Contributions

The contributions of this repository are engineering-oriented rather than algorithmic:

- Adapt the ASAP densification pipeline from validation-only processing to trainval processing.
- Generate 12Hz densified metadata files for the nuScenes trainval split.
- Release the generated `.pkl` files for easier reuse.
- Provide a reproducible codebase for running the adapted densification pipeline.

## Repository Structure

```text
asap-nuscenes-trainval-densification/
├── ASAP/                         # Adapted ASAP codebase
├── assets/                       # Checkpoints or auxiliary files
├── configs/                      # Modified or additional config files
├── scripts/                      # Scripts for trainval densification
├── output_pkls/                  # Generated 12Hz nuScenes metadata files
├── docs/                         # Notes and reproduction records
├── .gitattributes                # Git LFS rules for large files
└── README.md
```

## Generated Files

The generated densified metadata files are stored under:

```text
output_pkls/
```

Example files:

```text
nuscenes_infos_train_12hz.pkl
nuscenes_infos_val_12hz.pkl
```

These files are generated from the nuScenes trainval split using the adapted ASAP pipeline.

## Usage

### 1. Clone This Repository

```bash
git clone https://github.com/<your-username>/asap-nuscenes-trainval-densification.git
cd asap-nuscenes-trainval-densification
```

### 2. Prepare nuScenes

Please download the official nuScenes dataset from the nuScenes website and organize it according to the expected ASAP / MMDetection3D directory structure.

Example:

```text
data/nuscenes/
├── samples/
├── sweeps/
├── maps/
├── v1.0-trainval/
└── ...
```

This repository does not include raw nuScenes sensor data.

### 3. Prepare Checkpoints

Place the required detection checkpoint under:

```text
assets/ckpts/
```

For example:

```text
assets/ckpts/full_centerpoint.pth
```

### 4. Run Trainval Densification

Run the modified densification pipeline according to your local paths and configs.

Example:

```bash
python scripts/run_nuscenes_trainval_densification.py
```

Please modify the script paths, data root, checkpoint path, and output directory according to your environment.

## Data Release Notes

This repository only releases modified code and generated metadata files. It does not include raw nuScenes images, LiDAR point clouds, maps, or official dataset files.

If you use or redistribute the generated `.pkl` files, please make sure to comply with the nuScenes license and data usage terms.

For large `.pkl` files, Git LFS is recommended:

```bash
git lfs install
git lfs track "*.pkl"
git add .gitattributes
```

## Acknowledgements

This repository is based on the original ASAP project. Thanks to the ASAP authors for their work on annotation densification.

We also thank the nuScenes and OpenMMLab communities for providing datasets, toolkits, and open-source resources.

## Citation

If you find this repository useful, please cite the original ASAP work and the nuScenes dataset.

This repository is only an unofficial adaptation and metadata release based on ASAP.

```

```