# BtBot

Our work is to generate a behavior tree program consistent with the positive and negative example specifications from the natural language description provided by the user.

Our work has been deployed in dockers. Download our dockers through the following command

`docker pull btbot123/btbot`

In this dockers, the experimental part of the BtBot paper has been packaged into executable files. Next, we will introduce the use of executable files in detail.

When running the executable file, you need to prepare the following resources:

--url "https:// * * * " The address of the LLM called

--key " * * * " --llm "gpt-4o" The API key for calling LLM

Enter the project directory:

```
cd /BTBOT
```

## demo

For the automatic charging task in the paper, you can use the following command to view the running results of BTBOT.

`./dist/main_pre_check_change --task "demo" --url "https:// * * * " --key " * * * " --llm "gpt-4o" --data-path "/BTBOT/data"`

In this example, the output is:

['?', ['>', 'lowBattery', ['?', 'atCharge', 'goToCharge'], 'charging'], 'doOtherTask']

In addition, if you want to try to solve other tasks, such as: charge, ballFound, doTask, findfood, firefighting, please modify the task field in the command to solve the corresponding task.

### BTBOT effect

#### benchmark

The benchmark used in this work contains 70 tasks with different difficulties and scenarios. Please use the following command to view the distribution of the benchmark.

`python box2.py`

The program execution will get a benchmark.pdf file.

#### BTBOT robustness to different LLMs

In this work, the impact of LLMs with different performance on BTBOT is discussed. Execute the following command to view the impact of different LLMs on BTBOT and compare it with the effect of LLM generating BT programs. Among them, the files that the executable file depends on are located in the BTBOT/data directory.

`./dist/main_LLM3 --result "result" --url "https:// * * * " --key " * * * " --llm "gpt" --data-path "/BTBOT/data"`

The executable file will eventually output a piece of latex code, corresponding to the result shown in Figure 10.

## Baseline

#### Comparison with fine-tuning LLM baseline

First, we compare with the existing LLM fine-tuning technology BTGenBot. On the test set of BTGenBot, we use BTBOT to solve these tasks. You can view the output of BTBOT on the test set through the following command.

`./dist/main_BTGENBOT --result "result" --url "https:// * * * " --key " * * * " --llm "gpt-4o" --data-path "/BTBOT/data"`

#### Comparison with other BT generation baselines

In addition, we also compare with the existing work (MCTS-Syn) that generates BT using Monte Carlo tree search technology and the baseline that directly generates BT using LLM. Use the following command to view the latex code corresponding to the operation and results of the experiment.

`./dist/baseline --result "result" --url "https:// * * * " --key " * * * " --llm "gpt-4o" --data-path "/BTBOT/data"`

## Ablation Study

In this work, we proposed three key technologies, which resulted in five BTBOT variants. You can view the running results and effect display by executing the following command.

`./dist/ablation --result "result" --url "https:// * * * " --key " * * * " --llm "gpt-4o" --data-path "/BTBOT/data"`

Since the paper uses latex to draw pictures, Python is used here to draw pictures, which may be slightly different, but the data and effect display are not much different.

## User Study

We recruited 12 professional and non-professional behavior tree users to conduct user tests by handwriting target behavior trees and using BTBOT to generate behavior trees. The results are stored in the /BTBOT/data directory. Experimental results show that BTBOT is very helpful in helping users generate desired BTs.
