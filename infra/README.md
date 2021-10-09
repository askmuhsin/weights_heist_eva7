## Setup wandb.ai for nb runs
```python
!pip install wandb -qqq
import wandb
```
Add the above to the first cell ^ 

<br>
then you need to login to the environment -- 
```python
wandb.login()
```
at this step there will be prompts to enter the auth API key. Which you can get by going to this link -- https://wandb.ai/authorize 
<br>_Note: this step requires you to have activated your wandb.ai account_

<br>
```python
wandb.init(
    project='test_wandb',              ## unique to each project / assignment
    entity='weights_heist_eva7',       ## this will not change
    ## below are optional but recommended 
    tags=['muhsin'],                   ## can help later to filter runs
    name='my first test of env',       ## a name for the run. 
    dir='./data'                       ## store the runs locally in this dir
)
```
in wandb there are two conecpts we need to familiarize. "Runs" and "Projects".
<br>"Projects" are essentially a new assignment we start. for example the mnist+sum assignment. 
<br>but for this project there can be several "Runs" like trying out different loss fns, or preprocessing, or more dataset and so on.
<br>the idea is with wandb.ai we will be able to compare the different "Runs" to push forward our work. Each of us can create different runs and compare the results too.
<br>
Above snippet shows how a new run will have to be initialized.

During the run you can pretty much log any metrics related to the experiment.
<br>wandb offers an exhaustive list of options to log -- [documentation](https://docs.wandb.ai/v/master/library/log#:~:text=You%20can%20pass%20a%20matplotlib,pass%20the%20plot%20into%20wandb.)
<br>but most of the times we will be logging loss, and accuracy metrics which is as easy as -- 
```python
wandb.log({"acc": acc, "loss": loss})
```

once the experiment is done we can end the logging by -- 
```python
wandb.finish()
```

