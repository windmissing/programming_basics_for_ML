电子书阅读地址：https://windmissing.github.io/programming_basics_for_ML/  


可能有用的库：  

```python

import gc
import random
from pathlib import Path
from collections import defaultdict, Counter

from PIL import Image
import scipy as sp

import sklearn.metrics
from sklearn.metrics import accuracy_score
from sklearn.model_selection import StratifiedKFold

from functools import partial

from torch.optim.lr_scheduler import CosineAnnealingLR, ReduceLROnPlateau
from torch.utils.data import DataLoader, Dataset
import torchvision.models as models

from typing import Callable, List
```