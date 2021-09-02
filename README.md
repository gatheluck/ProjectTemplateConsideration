# Project Template Consideration

## Summary
### Strongly Recommended
- Create project template, maybe using some tool like `Cookiecutter` might be better.
- Change the way to handle path, specially about `data` and `ouput`.
- Use `pytest` and write some test code for lower layer objects.
- Use `Final` type hint.

### Recommended
- Use `pathlib.Path` to handle path instead of `os.path`.
- Use `pyproject.toml` file to manage package and setting of dev tools, like mypy.
- Use more functioal package manager like `poetry`. 
- Add some task runner, like `make` or `invoke`.

### Soso
- Following LightningModule official best practice.



## Detail

### pyproject.toml
- pyproject.toml is officially proposed in [PEP 517](https://www.python.org/dev/peps/pep-0517/) and [PEP 518](https://www.python.org/dev/peps/pep-0518/).
 the format file that defines the data needed to build the package proposed in PEP.


### LightningModule style guide
- Pytorch Lightning release official detail [style guide](https://pytorch-lightning.readthedocs.io/en/latest/starter/style_guide.html).


### Where to write dev tools setting

#### flake8
- [Official docs is here](https://flake8.pycqa.org/en/latest/user/configuration.html#configuration-locations).
- Setting should be written in one of `setup.cfg`, `tox.ini`, or `.flake8`.

#### mypy
- [Official docs is here](https://mypy.readthedocs.io/en/stable/config_file.html#the-mypy-configuration-file).
- Serching order is `mypy.ini` > `pyproject.toml` > `setup.cfg`.

### [PyTorch Lightning style guide](https://pytorch-lightning.readthedocs.io/en/stable/starter/style_guide.html)
- To increase reusability and scalability, LightningModule shoule define system not model.
```python
class LitModel(LightningModule):
    def __init__(self, encoder: nn.Module = None, decoder: nn.Module = None):
        super().__init__()
        self.encoder = encoder
        self.decoder = decoder
```

- Method order should be like below.
```python
class LitModel(pl.LightningModule):

    def __init__(...):

    def forward(...):

    def training_step(...):

    def training_step_end(...):

    def training_epoch_end(...):

    def validation_step(...):

    def validation_step_end(...):

    def validation_epoch_end(...):

    def test_step(...):

    def test_step_end(...):

    def test_epoch_end(...):

    def configure_optimizers(...):

    def any_extra_hook(...):
```

- If it is possible make `forward` and `training_step` independent. However when using DataParallel, you will need to call `forward` manually in side of `training_step`.