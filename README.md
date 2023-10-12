# gorilla-cli-testing

Testing of gorilla cli tool on Artemis HPC. 

## Installation 

Clone the repo 

```default
git clone https://github.com/gorilla-llm/gorilla-cli.git
```

Install with pip 

```default
module load python/3.9.15

pip install gorila-cli
```

Add local bin to PATH 

```default 
export PATH=$HOME/.local/bin:$PATH

source ~/.bashrc

source ~/.bash_profile
```

## Testing command-line 

Example provided in [documentation](https://github.com/gorilla-llm/gorilla-cli#usage) 

```default 
gorilla generate 100 random characters into a file called test.txt
```

Provided a few options and asked for selection: 

```default 
Welcome to Gorilla-CLI! Enhance your Command Line with the power of LLMs!

Simply use `gorilla <your desired operation>` and Gorilla will do the rest. For instance:
    gorilla generate 100 random characters into a file called test.txt
    gorilla get the image ids of all pods running in all namespaces in kubernetes
    gorilla list all my GCP instances

A research prototype from UC Berkeley, Gorilla-CLI ensures user control and privacy:
 - Commands are executed only with explicit user approval.
 - While queries and error (stderr) logs are used to refine our model, we NEVER gather output (stdout) data.

Visit github.com/gorilla-llm/gorilla-cli for examples and to learn more!
Use your Github handle (georgiesamaha@gmail.com) as user id? [Y/n]: y
??  Welcome to Gorilla. Use arrows to select
 » echo $(echo $(head /dev/random | tr -dc A-Za-z0-9 | head -c 100 > test.txt);cat test.txt;)
   cat /dev/urandom | tr -dc 'a-zA-Z0-9' | fold -w 100 | head -n 1 > test.txt
   echo "100 random characters" | tee test.txt
   : #Do nothing
```

```default
cat test.txt

```default
SNJHxSl5equMDoxQzDpBBTAJpGfYSluo3YDlbc24TQSDof5LEd53VADg1c2aOAOmZGOUtigctT8woA5OVcV9jDkdN58b2kurQroH
```

## Playground  

```default
gorilla load the module i need to run this command: samtools view file.bam
```

```default
??  Welcome to Gorilla. Use arrows to select
 » module load samtools
   module load samtools && samtools view file.bam
   module load samtools/samtools
```

```default 
gorilla load the module i need to run this script getfilepaths.py
```

```default
??  Welcome to Gorilla. Use arrows to select
   source "$(python -m site --user-site)/bin/activate.fish" && python getfilepaths.py
   `import os; os.load_module('getfilepaths.py') `
 » module load python && python getfilepaths.py
   : #Do nothing
```

```default
gorilla-cli-testing]$ gorilla write me a script with PBS pro job scheduler headers that can be submitted to the defaultQ and request 10GB memory and 5 cpus
```
```default
??  echo -e "#!/bin/bash\n#PBS -q defaultQ\n#PBS -l select=1:ncpus=5:mem=10GB" > pbs_script.sh
```

pbs_script.sh
```bash
#!/bin/bash
#PBS -q defaultQ
#PBS -l select=1:ncpus=5:mem=10GB
```

```default 
gorilla add to that pbs_script.sh a samtools command to extract reads from a specific region in my bam file and save to a new one. The region is on chromosome 5 from position 100 to 20000
```
```default
??  echo "samtools view -b input.bam 5:100-20000 > output.bam" >> pbs_script.sh
```