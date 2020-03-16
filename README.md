# Naive Bayes Transaction Classifier
This project uses a naive Bayes classification algorithm to assign a correct description and category to my personal finance transactions. I'm going to try using bag of words frequency features, or maybe bag of N letters, to land on the correct descriptions. Not sure about categories yet.

I'll also need a feedback loop to grab the least certain classifications, correctly map them, then add them to the training dataset.

But let's begin with the dockerfile.

## Dockerfile
I have included 2 dockerfiles that work (so far).

### `continuumio/anaconda3`
This image is built from the Continuumio Anaconda3 docker image. The dockerfile uses a tini `ENTRYPOINT` and runs a Jupyter notebook.

Build the image with:
```
docker build -t <image_name> ~/...path/...to/...dockerfile
```

Run the container with:
```
docker run -it -p 8888:8888 -e JUPYTER_TOKEN=ztoken <image_name>
```

### `jupyter/datascience-notebook`
This image is built from the Jupyter Datascience-Notebook image. I installed `nltk` in the dockerfile, but I skipped the `ENTRYPOINT` argument in favor of simply using the `--init` flag at runtime.

Build the image with:
```
docker build -t <image_name> ~/...path/...to/...dockerfile
```

Run the container with:
```
docker run -it -p 8888:8888 --init -e JUPYTER_TOKEN=ztoken <image_name>
```
