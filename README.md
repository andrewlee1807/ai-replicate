# ai-replication

## Checkout at: **https://pypi.org/manage/project/aireplication/releases/**

## Usage
```python
from aireplication.ultils.data import TimeSeriesGenerator, Dataset

config = {"dataset_name": "CNU",
          "features": ["전력사용량"],
          "input_width": 168,
          "output_length": 1,
          "train_ratio": 0.9
          }

dataset = Dataset(dataset_name=config["dataset_name"])
# data = dataset.dataloader.export_a_single_sequence()
data = dataset.dataloader.export_the_sequence(config["features"])

print("Building time series generator...")
tsf = TimeSeriesGenerator(data=data,
                          config=config,
                          normalize_type=1,
                          shuffle=False)

```

## Publishing the package
```shell
pip install twine
python setup.py sdist
twine upload dist/*
```

**- Note: Testing case:**
```shell
twine upload --repository testpypi dist/*
```