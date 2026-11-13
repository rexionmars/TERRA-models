# TERRA models

Trained land-cover classifiers for [TERRA](https://github.com/rexionmars/TERRA),
published as model packages. TERRA lists them on its **Models** screen from
`catalog.json` in this repository, and installs a package only after its zip
matches the SHA-256 the catalogue gives for it.

| Model | Package | Size | Needs | Zip SHA-256 |
|---|---|---|---|---|
| Random Forest 1.0.0 | [`spectral-1.0.0.zip`](https://github.com/rexionmars/TERRA-models/releases/tag/spectral-1.0.0) | 14.8 MB | | `cdced7833e6d752087463b6285e676cf86128659bebda6e09497cfe49c2b311c` |
| Temporal Transformer 1.0.0 | [`temporal_transformer-1.0.0.zip`](https://github.com/rexionmars/TERRA-models/releases/tag/temporal_transformer-1.0.0) | 1.7 MB | `torch` | `8710f22daa797397c232e7ba524e73cc197034ae0e0a2f4a936c3eb7f5cb775c` |

Both classify Sentinel-2 L2A series into the MapBiomas classes 3, 21, 25, 39 and
41, and were fitted for western Paraná. Each package's `model.json` states what
the model reads, how it works, how it was evaluated and its limits; TERRA shows
the same on the model's page.

## Installing

In TERRA, open **Models**, choose a model and **Download and install**. A
package downloaded by hand installs through **Import a package**.

## Format

A package is a flat zip: `model.json` and the files it names, each with its
SHA-256 and size. TERRA checks every file against the manifest when it installs
the package and again before every run, because the weights are pickles and
loading one runs code. The format is described in TERRA's
[docs/ARCHITECTURE.md](https://github.com/rexionmars/TERRA/blob/main/docs/ARCHITECTURE.md#model-packages).

`catalog.json` and the zips are written by TERRA's `scripts/package_models.py`,
which makes reproducible zips; neither is edited by hand.

## Licence

The weights are released under the MIT licence, in [LICENSE](LICENSE). They were
trained against land-cover maps of the [MapBiomas](https://brasil.mapbiomas.org)
project, which are published under CC BY 4.0. Each card picture is credited in
its package's `model.json`.
