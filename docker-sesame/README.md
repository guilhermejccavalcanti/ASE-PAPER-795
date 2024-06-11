## Initial setup

1. Ensure Docker is installed and updated on your machine. Confirm by running `docker -v` in the terminal.
2. Copy the `docker-sesame` folder from this replication package to your machine. It contains all the necessary infrastructure for the experiment.
3. Navigate to the `docker-sesame` folder.

## Build the Experiment’s Container Image

Run `docker build -t docker-sesame .` to build a new container image using the `Dockerfile`.

> The `-t` flag tags our image, providing a human-readable name for the final image.

> The `.` at the end of the docker build command indicates that Docker should look for the `Dockerfile` in the current directory.

## Start the Experiment Container

Start your container using the `docker run` command and specify the name of the image created:

Run `docker run --rm -it docker-sesame bash`

> Docker will run the container, detach it (run it in the background), and attach an interactive terminal, similar to a virtual machine. Note that this will run a shell instead. Effectively, you will have a container that stays running permanently.

## Running the Experiment

To run the experiment, use the following command:

`gradle run --args="-i injectors.S3MWithCSDiffMiningModule projects.csv Results"`

> `projects.csv` is the file containing our sample projects' GitHub repositories, located in the `/miningframework/` folder from this replication package.

> `Results` is a folder generated during the execution of the experiment.

#### To Copy the Result Files to Your Machine:

1. Open another terminal while keeping the first one open.
2. Run the command: `docker run --rm s3misi; $CONTAINERID = $(docker ps -alq); docker cp $CONTAINERID/:/home/miningframework/Results ./Results` 
3. The `Results` folder from the container is now copied to your machine. It contains:
   - A `results.csv` file aggregating the metrics of the experiment.
   - A folder for each project in our sample, containing the merge scenarios and the output of the merge tools for each merged file.
