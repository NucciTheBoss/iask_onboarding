## Slide 7 (Interactive Example Time)
In order to ensure that everything goes according to plan, ensure that you have the following dependencies installed:

* [Oracle Virtual Box](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html)
* [Vagrant](https://www.vagrantup.com/downloads)

Once these are installed, you will be ready to go to set up the Singularity VM!

## Slide 8 (Set up your build environment!)
Open the terminal on your computer and then enter the following commands to create and start the Singularity VM (in my case I am using the [Windows terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab)):

```bash
cd D:\VMs
mkdir SINGULARITY
cd SINGULARITY
vagrant init sylabs/singularity-3.5-centos-7-64 --box-version 20191206.0.0
vagrant up
```

## Slide 9 (Time to build your container!)
Use the following commands to build the Singularity container inside the VM:

```bash
vagrant ssh  #=> Connect to the Singularity VM
git clone https://github.com/NucciTheBoss/iask_onboarding_spring_2021.git
cd iask_onboarding_spring_2021/day_2
sudo singularity build image.sif R-4.0.3.rstudio.def  #=> sudo password is "vagrant"
```

*In order for the demonstration to work, have Interactive Desktop Session running and then use the following command to upload the Singularity container to Roar:*

```bash
scp image.sif jcn23@datamgr.aci.ics.psu.edu:~/scratch
```

*It's going to take a litle bit to upload the container, so handle this before the presentation.*

## Slide 10 (Demonstration!)
Connect to your Interactive Desktop Session, and then use the following commands to launch RStudio:

```bash
cd ~/scratch
singularity -s exec image.sif rstudio &> /dev/null
```

**Warning:** It will take a little bit for RStudio to launch!

## Slide 11 (Where should you go from here?)
Take this time to ask everyone questions, and be sure to walk through what a Docker file looks like.

**Warning:** You're probably going to be asked a lot of questions so be prepared[^1]!

[^1]: For future reference, I think this presentation needs to be extended a bit. Personally, I would like more time to focus on Docker and not all on Singularity. I would also like for time to focus on using the Cloud components of Singularity and Docker. The Sylabs Library and Docker Hub are powerful tools! Next time, demonstrate pushing Singularity container to the cloud, and show all the options you have on Docker Hub!