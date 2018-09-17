# Docker

### Dockerfile

```
FROM broadinstitute/genomes-in-the-cloud:2.3-1498756809
RUN echo "r <- getOption('repos'); r['CRAN'] <- 'http://cran.us.r-project.org'; options(repos = r);" > ~/.Rprofile
RUN Rscript -e "source('http://bioconductor.org/biocLite.R'); biocLite('DNAcopy')"
MAINTAINER Mimoun Cadosch<mimoun@broadinstitute.org>
```

---

### Uploading your image to docker

1. Build your docker image:  
   `docker build -t mcadosch/tsca .`

2. Tag your image according to your dockerhub image name:  
   `docker tag tsca mcadosch/tsca`

3. Push the image:  
   `docker push mcadosch/tsca`

---

### Running Docker locally

* Run program: 
  ```
  docker run --rm -i -v \
    $PWD:$PWD -w $PWD \
    tsca python  aggregate_depth_of_cov_output.py AA66-Tumor-SM-    F29RQ.sample_interval_summary
  ```
* Run interactively:
  ```
  docker run --rm -i -t imagename
  ```

* Run interactively and copying current file system:
```
docker run --rm -i -v $PWD:$PWD -w $PWD -t mcadosch/tsca
```
  ----
  ### Workflow

Each Firecloud workflow has a corresponding directory in the TSCA Firecloud github repo.

1. Write your script locally
2. Test your script locally
3. Test your script with Docker
4. Upload Docker
5. Write and test Firecloud workflow
6. Add link to Github repo for corresponding workflow

---

### Working from other images

In `Dockerfile`, specify `FROM imagename` and add your libraries, scripts, etc.

---



