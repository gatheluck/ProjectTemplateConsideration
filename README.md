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


### LightningModule best practice
- Pytorch Lightning release official detail [best practice style guide](https://pytorch-lightning.readthedocs.io/en/latest/starter/style_guide.html). e.g.) If you want to increase reusability and scalability, LightningModule shoule define system not model.