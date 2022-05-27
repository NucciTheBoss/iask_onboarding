## Slide 5 (Termius in Action)
While ssh'd into `submit.aci.ics.psu.edu`, execute the following command:

```bash
find $(pwd) -type f -print0 | xargs -0 dos2unix --
```

This will convert all the files in the current directory to UNIX format. That being said, since this command is so long and you will use it often, it is better save it as a snippet.

*Demonstrate saving the above command as a snippet and then execute it on the command line*

---

## Slide 11 (WSL2 in Action)
Let's say a user needs some help utilizing a few commands. We can use `ps2pdf` to help this individual, but we don't want to go through the hassle of pulling the pdfs off of the cluster. Therefore, activate WSL2 (open Windows Terminal, enter Crtl+Shift+3 on keyboard). Once WSL2 has been opened, enter the following commands into the command prompt:

```bash
cd /mnt/d/scratch
man -t cat | ps2pdf - cat.pdf
man -t parallel | ps2pdf - parallel.pdf
man -t chmod | ps2pdf - chmod.pdf
```

After these commands have been executed, demonstrate that these pdfs can then be accessed from the Windows operating system. *If feeling fancy, create a tar archive in WSL2 as well*

---

## Slide 13 (Vagrant in Action)
Say you want to create a base installation of Centos 7 to test some software out on. Well, Vagrant is your homie. Open Windows Powershell and the execute the following commands:

```
cd D:\VMs\CENTOS7
vagrant up
vagrant ssh
```

At this point, you should know be inside the Centos 7 VM. Demonstrate that you are inside a Centos 7 VM, and then download and build zlib inside the container:

```bash
cat /etc/os-release
wget https://www.zlib.net/zlib-1.2.11.tar.gz
tar -xzvf zlib-1.2.11.tar.gz
cd zlib-1.2.11
./configure --prefix=$HOME/sw7/zlib
make && make install
```

After you verify that zlib was successfully installed, exit the VM and shut it down:

```
exit
vagrant halt
```

---

## Slide 18 (Anaconda in Action)
Demonstrate the awesome power of the conda package manager. Try running the following commands on `submit.aci.ics.psu.edu`:

```bash
conda activate beautify
python beautify.py -f data.csv
```

Now watch as it fails miserably. That's because you don't have `click` or `tabulate` installed. To fix this, run the following commands and try again:

```bash
conda install -c conda-forge tabulate click -y
python beautify.py -f data.csv
```

Now watch as your beautiful data is printed out to the command line!
