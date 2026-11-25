<h1 align="center">DBB_ANTsCortThickSeg</h1>

<p align="center">
  Segments brain tissues in a T1-weighted image with a customized ANTs antsCorticalThickness.sh using Pediatric Template of Brain Perfusion (PTBP) priors and an optional brain mask, and outputs a tissue segmentation.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.541"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.541-blue.svg" alt="Run on brainlife.io"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Segments brain tissues in a T1-weighted image with a customized ANTs antsCorticalThickness.sh using Pediatric Template of Brain Perfusion (PTBP) priors and an optional brain mask, and outputs a tissue segmentation.**

Runs stages 1-3 of a customized antsCorticalThickness.sh (ANTs 2.2.0) with the PTBP template and six tissue priors bundled in the repo; when a brain mask is given it replaces the template-based brain extraction. Developed for the Distorted Brain Benchmark (DBB) of paediatric patients with brain malformations. It needs a T1w image; the output is the ANTs BrainSegmentation volume with a label.json.

| | |
|---|---|
| **Inputs** | `neuro/anat/t1w` · `neuro/mask` (optional) |
| **Outputs** | `neuro/parcellation/volume` |
| **Container** | `brainlife/ants:2.2.0-1bc` |
| **Resources** | 10 CPUs |
| **Run it** | [doi.org/10.25663/brainlife.app.541](https://doi.org/10.25663/brainlife.app.541) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `t1` | `neuro/anat/t1w` | yes | T1-weighted image to segment. |
| `mask` | `neuro/mask` | no | Optional brain mask used instead of the template-based brain extraction. Must be in the same space as the T1. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `segmentation` | `neuro/parcellation/volume` | Brain tissue segmentation (segmentation.nii.gz, ANTs BrainSegmentation) with label.json. |

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.541](https://doi.org/10.25663/brainlife.app.541), choose `neuro/anat/t1w`, `neuro/mask` from your project and press **Execute**. The results are saved to your project as `neuro/parcellation/volume`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `brainlife/ants:2.2.0-1bc`), [`jq`](https://jqlang.github.io/jq/).

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "t1": "/path/to/t1/t1",
       "mask": "/path/to/mask/mask"
   }
   ```

3. Run `./main`.

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- DBB_ANTsCortThickSeg. brainlife.io App. [doi:10.25663/brainlife.app.541](https://doi.org/10.25663/brainlife.app.541)
- Amorosino G, Peruzzo D, Redaelli D, Olivetti E, Arrigoni F, Avesani P. DBB - A Distorted Brain Benchmark for Automatic Tissue Segmentation in Paediatric Patients. NeuroImage 119486 (2022). [doi:10.1016/j.neuroimage.2022.119486](https://doi.org/10.1016/j.neuroimage.2022.119486)
- Avants et al. A reproducible evaluation of ANTs similarity metric performance in brain image registration. *NeuroImage* 54:2033-2044 (2011). [doi:10.1016/j.neuroimage.2010.09.025](https://doi.org/10.1016/j.neuroimage.2010.09.025)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

Gabriele Amorosino
