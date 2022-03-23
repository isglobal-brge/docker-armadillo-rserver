FROM datashield/armadillo-rserver:2.0.0

# Install OD dependencies
RUN apt-get install liblzma-dev libicu-dev -y

# Install littler to use BioConductor Manager
RUN install2.r --error BiocManager littler --repos "https://cloud.r-project.org/"
RUN ln -s /usr/local/lib/R/site-library/littler/examples/installBioc.r /usr/local/bin/installBioc.r 

# Install dsExposome dependencies
RUN installBioc.r rexposome

# Install dsBase package
ENV DS_DEP_VERSION "6.1.1"
RUN installGithub.r "datashield/dsBase@${DS_DEP_VERSION}"

# Install dsExposome package
ENV DS_PKG_VERSION "2.0.2"
RUN installGithub.r "isglobal-brge/dsExposome@${DS_PKG_VERSION}"

CMD R -e "MolgenisRserve::Rserve(debug=${DEBUG}, args='--vanilla --RS-set remote=enable --RS-set auth=disable --RS-set daemon=disable')"
