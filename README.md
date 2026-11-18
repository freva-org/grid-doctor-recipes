# Grid Doctor recipes

This repository contains the dataset-specific workflows used to generate
HEALPix datasets with the [Grid Doctor](https://github.com/freva-org/grid-doctor)
library. It does not contain the Grid Doctor library itself.

Each recipe documents how a particular source dataset is opened, remapped,
written, and, where applicable, published. Recipes may include Python scripts,
workflow configuration, batch-job helpers, and exploratory notebooks.

The generated datasets can be explored in the
[Waterpark data browser](https://waterpark.dkrz.de/databrowser/).

## Recipes

| Dataset | Workflow |
| --- | --- |
| [CMIP6](recipes/cmip6/) | Reflow/Slurm conversion workflow |
| [EERIE](recipes/eerie/) | EERIE remapping and rechunking workflow |
| [ERA5](recipes/era5/) | ERA5 regridding workflow |
| [ICON-DREAM](recipes/icon-dream/) | Reflow/Slurm and direct conversion workflows |
| [NextGEMS](recipes/nextgems/) | Data-transfer and rechunking notebooks |
| [ORCESTRA](recipes/orcestra/) | Zarr-writing notebook |

See the README in each recipe directory for dataset-specific prerequisites,
configuration, and execution instructions.

## 🏥 Grid Rehab Progress

How are our patients doing? Every dataset starts broken and leaves HEALed. If
your dataset is still 😢, it needs a doctor — that could be you. Claim a
patient, write a recipe, and turn that frown into 😎.

| Meaning | |
| --- | --- |
| 😢 | Not started |
| 🩹 | In treatment |
| 😎 | HEALed |

| Dataset | Uploaded to S3 | Recipe submitted |
| --- | --- | --- |
| ICON-DREAM | 😎 | 😎 |
| EERIE | 😎 | 😎 |
| ERA5 | 😎 | 😎 |
| CMIP6 | 🩹 | 😎 |
| NextGEMS | 😎 | 😎 |
| ICDC | 😎 | 🩹 |
| ORCESTRA | 😎 | 😎 |
| PalMod | 😢 | 😢 |
| DYAMOND | 😎 | 😎 |
| EarthCARE | 😢 | 🩹 |

> [!TIP]
> To claim a dataset, add a recipe under `recipes/<dataset>/` and update this
> table.

## Using a recipe

Recipes depend on the Grid Doctor library and may additionally require access
to their source data, HPC resources, object storage, or dataset-specific
credentials. Install the dependencies declared by the recipe you intend to run
and follow its instructions. Do not commit credentials or access keys.

For Grid Doctor installation and library documentation, visit the
[Grid Doctor repository](https://github.com/freva-org/grid-doctor) and its
[documentation](https://freva-org.github.io/grid-doctor/).

## Contributing

Add or update a recipe in `recipes/<dataset>/`, including a README that
explains its purpose, prerequisites, invocation, outputs, and known
limitations.

## Development checks

This repository uses [pre-commit](https://pre-commit.com/) for lightweight
checks shared by every recipe. Install the hook after cloning:

```console
python -m pip install pre-commit
pre-commit install
```

Run all checks manually with:

```console
pre-commit run --all-files
```

The checks validate YAML, prevent common formatting and merge-conflict
mistakes, detect accidentally committed private keys, and run `codespell`.
Recipe-specific tests and dependencies remain documented in each recipe.

## Writing a conversion recipe

Create a directory for the dataset and add a conversion script:

```console
mkdir -p recipes/<dataset>
```

The script should use the [Grid Doctor](https://github.com/freva-org/grid-doctor)
library to open the source data, create the HEALPix pyramid, and write the
result. Add a README describing the recipe's goal, prerequisites, invocation,
outputs, and known limitations. Include any workflow configuration or batch-job
helpers necessary to run it reproducibly.

> [!IMPORTANT]
> Please add a descriptive README for every recipe and document problems or
> limitations encountered while producing the dataset.

> [!CAUTION]
> Do not commit S3 access keys, secrets, or other credentials to this
> repository. Use environment variables or a credentials file instead.

## License

This project is licensed under the [GNU Affero General Public License v3.0](LICENSE).
