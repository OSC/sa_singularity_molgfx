# Singularity Molgfx

[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/3587)
[![GitHub License](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

Singularity image for [Open Chemistry](https://github.com/OpenChemistry), Gabedit and Jmol. It was built on top of the base Docker image [ubuntu](https://hub.docker.com/_/ubuntu).

## Build

You can build a local Singularity image named `molgfx.sif` with:

```sh
sudo singularity build molgfx.sif Singularity
```

## Deploy

Instead of building it yourself you can download the pre-built image from [Singularity Hub](https://www.singularity-hub.org) with:

```sh
singularity pull molgfx.sif shub://OSC/sa_singularity_molgfx
```

## Run
### Find versions of molecular graphics systems
```sh
singularity inspect -H molgfx.sif
```

### Start Avogadro2
Avogadro2 is started using the default exec command:
```sh
singularity exec molgfx.sif avogadro2
```

## License

The code is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
