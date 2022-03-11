# RServer Armadillo containers
This repository contains the different analysis environments for the Armadillo DataSHIELD platform.

Currently we support these analysis environments:

Production
- Exposome environment [dsExposome](https://github.com/isglobal-brge/dsExposome)
- Omics environment [Omics](https://github.com/isglobal-brge/dsOmics)

Development
- NA

You can use these images to support different analysis environments on the Armadillo backend.
## Development
We define 2 environment in development of these images.

- production == R-packages can be used as production environments for the cohorts
- development == R-packages are not released yet and/or work only with the development version of the dsBase package

## Building and publishing
We use a pipeline mechanism to build these images.
