FROM datashield/armadillo-rserver:2.0.0

# Install OS dependencies for dsOmics
RUN apt update
RUN apt install liblzma-dev libicu-dev libxml2 -y

# Install littler to use BioConductor Manager
RUN install2.r --error BiocManager littler --repos "https://cloud.r-project.org/"
RUN ln -s /usr/local/lib/R/site-library/littler/examples/installBioc.r /usr/local/bin/installBioc.r 

# Install resourcer package (this is needed because the Armadillo needs it during boot)
ENV RESOURCER_VERSION "1.1.1"
RUN install2.r --error httr --repos "https://cloud.r-project.org/"
RUN install2.r --error "https://cloud.r-project.org/src/contrib/resourcer_${RESOURCER_VERSION}.tar.gz" --repos NULL

# Install S3 resourcer
ENV DS_DEP_S3_VERSION "HEAD"
RUN installGithub.r "molgenis/s3.file.resourcer@${DS_DEP_S3_VERSION}" --deps=TRUE

# Install dsBase package
ENV DS_DEP_VERSION "6.1.1"
RUN installGithub.r "datashield/dsBase@${DS_DEP_VERSION}" --deps=TRUE

# Install dsOmics package
ENV DS_PKG_VERSION "v1.0.17"
RUN installGithub.r "isglobal-brge/dsOmics@${DS_PKG_VERSION}" --deps=TRUE

CMD R -e "MolgenisRserve::Rserve(debug=${DEBUG}, args='--vanilla --RS-set remote=enable --RS-set auth=disable --RS-set daemon=disable')"
