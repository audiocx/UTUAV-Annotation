# UTUAV-Annotation

Work related to annotation process of the UTUAV datasets.

## How to replicate the workspace

We are currently using CVAT as our annotation tool, it enables us to export the dataset in multiple formats. It also allows multiple people to collaborate on different annotation tasks when the ports are exposed to the internet.

For a full installation tutorial you can visit the official [installation guide](https://docs.cvat.ai/docs/administration/basics/installation/), but here's an overview on how to do it:

What you need:

- Docker
- Git

Guide:

- Clone the official CVAT repository:
  - `$ git clone https://github.com/cvat-ai/cvat`
- Enter the folder:
  - `$ cd cvat`
- Compose the Docker containers:
  - `$ sudo docker compose up`
- Access the cvat_server bash:
  - `$ docker exec -it cvat_server bash`
- Create a superuser:
  - `$ python manage.py createsuperuser`
    Here you will be required to input an username, email address and a password, these are gonna be the credentials to access CVAT from the web browser.
- If everything went right, you should be able to access CVAT on localhost:8080.
- You can login with your previously created credentials.

Once CVAT is already running on port 8080, to import the datasets do the following (we will use B dataset as an example):

- Download the B dataset from [here](https://drive.google.com/drive/folders/1mbIaqAaERiQfhhYHoR5-KsVYhSrRojXI?usp=sharing).
- We recommend importing via Pascal VOC 1.1 annotation format, this file is named "B_snapshot_dd-mm-yy_PascalVOC.zip", depending on the snapshot's date.
- Unzip this file with:
  - `$ unzip B_snapshot_dd-mm-yy_PascalVOC.zip`
- Since this .zip only has the annotations and ignores the images, it's your task to put all images listed in B_snapshot_dd-mm-yy_PascalVOC/ImageSets/Main/default.txt inside the folder B_snapshot_dd-mm-yy_PascalVOC/JPEGImages.
- Zip this file back with all the images, make sure you're inside the folder B_snapshot_dd-mm-yy_PascalVOC:
  - `$ zip -r B_snapshot_dd-mm-yy_PascalVOC.zip ./*`
- Go to CVAT in your web browser on localhost:8080.
- Go to "Projects" section on the navbar.
- Create a new project by pressing the blue button with the plus sign.
- Name your project, and press "Submit & open".
- Press the "Actions" button on the top-right, it's the one with three dots.
- Select import dataset, select Pascal VOC 1.1 for the import format.
- Upload the previously zipped file "B_snapshot_dd-mm-yy_PascalVOC.zip" and press OK.
- It should take around 30 minutes to upload and process the dataset.
- Once the dataset is ready, you can go to "Jobs" section on the navbar and select the annotation job you want to start annotating.
