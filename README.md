# Building and using a Docker Image/Container

* This example helps you create an image that:
    * is based on Ubuntu 18.04 (It has Python 3 already installed)
    * We will update Ubuntu and install the sklearn, pandas packages on it
    * Write a Python script that receives a CSV file, perform some calculations on it and write the results into a results file (e.g. `dataset.csv.out`)
    * This results file should be saved into our host machine (permanent)


Let’s build our image (you can choose your own tag):
`$ docker build -t linreg .`
and now we run the container passing it our dataset file and specifying the folder we want to the result to be stored in (using volumes):
`$ docker run -v /path/to/dockerfile/:/work/ linreg dataset.csv `

This `/path/to/dockerfile/` is the full path to your current directory on the host machine

This `/work/` is the directory inside the container (the script will write the results there)

the `dataset.csv` file will be automatically passed to the script as an `ENTRYPOINT` argument
