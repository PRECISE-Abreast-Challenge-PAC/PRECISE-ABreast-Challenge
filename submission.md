# Competition Submission Guidelines

## 📤 Submission Process

All participants must submit their models via **Codabench** using a **COG-compliant Docker container**. This ensures fairness, reproducibility, and automated evaluation.


## 🎯 Challenge Tasks

The challenge consists of two main tasks:

* **Task 1: Multi-Task Segmentation**
* **Task 2: Multi-Task Classification**

## 📋 Competition Phases

### Development Phase

Participants are required to design a single model that performs **multi-task learning**, simultaneously predicting the **breast-level diagnostic category** (no lesion, benign lesion, malignant lesion) and generating a **pixel-wise segmentation mask** of any visible lesion.

### Validation Phase

Participants submit their predictions for evaluation.

#### Submission Structure

Prepare a zip file for submission with the following structure:
##### ZIP structure for submission
```
submission.zip
│
├── classification.csv
└── segmentation/
    ├── PABC_00001_000_BUS_mask.png
    ├── PABC_00002_001_BRE_mask.png
    └── ...
```

#### Classification Results (`classification.csv`)

A CSV file with predictions for each image ID:

```csv
image_id,label
PABC_00001_000_BUS,Normal
PABC_00002_001_BRE,Benign
PABC_00003_002_BBR,Malignant
PABC_00004_100_ABR,Benign
PABC_00005_101_ABR,Malignant
```

### Test Phase

The participants are called to upload their method in a Cog container for evaluation on the test set.
#### 🐳 COG Container Structure

Your COG-compliant Docker container should include the following files:

```
cog-container/
│
├── cog.yaml                    # COG configuration file
├── predict.py                  # Main prediction script
├── model.py                    # Model architecture definitions
├── requirements.txt            # Python dependencies
├── models/                     # Model weights and files
│   ├── segmentation_model.pth
│   ├── classification_model.pth
│   └── ...
├── utils/                      # Utility functions (IF ANY)
│   ├── __init__.py
│   ├── preprocessing.py       
│   └── postprocessing.py      
└── Dockerfile                  # Optional: custom Docker setup
```
#### 📄 Example `cog.yaml`

```yaml
build:
  python_version: "3.12"
  system_packages:
    - "libgl1-mesa-glx"
    - "libglib2.0-0"
  python_packages:
    - "torch==2.2,1"
    - "torchvision==0.17.0"
    - "opencv-python==4.9.0.80"
    - "numpy==1.26.4"
    - "pillow==10.3.0"

predict: "predict.py:Predictor"
```
---

#### 📦 Example `requirements.txt`
> ✅ **Instruction:** Add all python dependencies to your `requirements.txt` file.
```txt
torch==2.2.1
torchvision==0.17.1
opencv-python==4.9.0.80
numpy==1.26.4
pillow==10.3.0
scipy==1.13.1
scikit-image==0.23.2
```


#### 🧠 Example `predict.py`

```python
import cog
import torch
import numpy as np
from PIL import Image
from pathlib import Path
from model import SegmentationModel, ClassificationModel
from utils.preprocessing import preprocess_image, preprocess_for_segmentation, preprocess_for_classification
from utils.postprocessing import postprocess_segmentation, postprocess_classification

class Predictor(cog.Predictor):
    def setup(self):
        """Load models and initialize"""
        # Initialize model architectures
        self.segmentation_model = SegmentationModel()
        self.classification_model = ClassificationModel()
        
        # Load trained weights
        self.segmentation_model.load_state_dict(torch.load('models/segmentation_model.pth'))
        self.classification_model.load_state_dict(torch.load('models/classification_model.pth'))
        
        self.device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
        self.segmentation_model.to(self.device)
        self.classification_model.to(self.device)
        
        # Set models to evaluation mode
        self.segmentation_model.eval()
        self.classification_model.eval()
    
    @cog.input("image", type=Path, help="Input medical image")
    def predict(self, image: Path) -> dict:
        """Run prediction"""
        
        # Load raw image
        raw_img = Image.open(image)
        
        # Preprocess image for both tasks
        seg_input = preprocess_for_segmentation(raw_img)
        cls_input = preprocess_for_classification(raw_img)
        
        # Run segmentation
        segmentation_mask = self.run_segmentation(seg_input)
        
        # Run classification
        classification_result = self.run_classification(cls_input)
        
        # Postprocess results (IF ANY)
        final_mask = postprocess_segmentation(segmentation_mask, raw_img.size)
        final_classification = postprocess_classification(classification_result)
        
        return {
            "segmentation_mask": final_mask,
            "classification": final_classification
        }
    
    def run_segmentation(self, preprocessed_image):
        """Perform tumor segmentation"""
        with torch.no_grad():
            input_tensor = preprocessed_image.to(self.device)
            output = self.segmentation_model(input_tensor)
            return output.cpu()
    
    def run_classification(self, preprocessed_image):
        """Perform classification"""
        with torch.no_grad():
            input_tensor = preprocessed_image.to(self.device)
            output = self.classification_model(input_tensor)
            return output.cpu()
```

#### 🧠 Example `model.py`

```python
import torch
import torch.nn as nn
import torch.nn.functional as F

class SegmentationModel(nn.Module):
    """U-Net model (Segmentation)"""
    def __init__(self, in_channels=3, out_channels=1, features=[64, 128, 256, 512]):
        super(SegmentationModel, self).__init__()
        
        # Encoder
        self.encoder = ""
        
        # Bottleneck
        self.bottleneck = ""
        
        # Decoder
        self.decoder = ""


        # Final layer
        self.final_conv = ""
    
    def forward(self, x):
        # Forward pass
        pass

class ClassificationModel(nn.Module):
    """ResNet model (Classification)"""
    def __init__(self, num_classes=3):  # Normal, Benign, Malignant
        super(ClassificationModel, self).__init__()
        
        # Feature extractor
        self.features = nn.Sequential(
            nn.Conv2d(3, 64, 7, 2, 3, bias=False),
            # Add more layers as needed
        )
        
        # Classifier
        self.classifier = nn.Sequential(
        )
    
    def forward(self, x):
        x = self.features(x)
        x = self.classifier(x)
        return x
```

#### 🛠️ Example Utility File: `utils/preprocessing.py`

```python
import torch
import numpy as np
from PIL import Image
import torchvision.transforms as transforms

def preprocess_for_segmentation(image):
    """Preprocess image (Segmentation)"""
    transform = transforms.Compose([
        transforms.Resize((256, 256)),

    ])
    return transform(image).unsqueeze(0)

def preprocess_for_classification(image):
    """Preprocess image (Classification)"""
    transform = transforms.Compose([
        transforms.Resize((224, 224)),
        transforms.ToTensor(),

    ])
    return transform(image).unsqueeze(0)
```

---

## 📦 Submission Limitations

- One submission per day during the validation phase  
- All submissions must be **COG-compliant Docker containers**  
- Submissions must follow the **exact file naming convention and structure** outlined above  

## 🔧 Technical Requirements

Your Docker container must:

- Be **COG-compliant** Docker container. This ensures fairness, reproducibility, and automated evaluation.
- Process images according to the **file naming convention**  
- Include **all python dependencies and model weights**