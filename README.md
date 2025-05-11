# doc-layout-parser

This project develops a layout parsing pipeline to extract key components (e.g., abstract, context, table, reference) from academic PDFs using a Detectron2-based model trained on annotations from Label Studio.

## 🔍 Purpose

To identify and segment document elements like titles, authors, abstracts, tables, figures, and references using object detection techniques, improving downstream analysis and semantic classification with LLMs.

## ⚙️ Features

- Fast R-CNN architecture (Detectron2) for layout detection
- Layout categories: Abstract, Author, Context, Header, Image, Reference, Sub-title, Table, Title
- Integration-ready with LLMs for content-based filtering or labeling
- Configuration through `config.yaml`

## 🗃 File Structure

- `config.yaml` - Detectron2 configuration for the layout model
- `result.json` - Output annotations from model inference
- `parsing.ipynb` - Sample notebook to run detection and visualize results

## 📦 Dependencies

Install via pip:
```bash
!pip install pycocotools
!pip install layoutparser
!pip install "layoutparser[effdet]"
!pip install layoutparser torchvision
!python -m pip install 'git+https://github.com/facebookresearch/detectron2.git'
!pip install layoutparser torchvision && pip install "git+https://github.com/facebookresearch/detectron2.git@v0.5#egg=detectron2"
!pip install "layoutparser[paddledetection]"
!pip install "layoutparser[ocr]"
```

Install via Conda:
```bash
conda install detectron2 pytorch opencv omegaconf hydra-core -c conda-forge
```

🚀 How to Run
```bash
# Inside parsing.ipynb
from layoutparser.models import Detectron2LayoutModel

model = Detectron2LayoutModel(
    config_path='config.yaml',
    extra_config=["MODEL.ROI_HEADS.SCORE_THRESH_TEST", 0.8],
    label_map={0: "Abstract", 1: "Author", ...}
)
```
📄 Annotation Categories
	•	Abstract
	•	Author
	•	Context
	•	Header
	•	Image
	•	Reference
	•	Sub-title
	•	Table
	•	Title
