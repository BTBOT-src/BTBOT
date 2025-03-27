# BtBot

Our work is to generate a behavior tree program consistent with the positive and negative example specifications from the natural language description provided by the user.

Our work has been deployed in dockers. Download our dockers through the following instructions

```docker pull btbot123/btbot```

In this dockers, the experimental part of the BtBot paper has been packaged into executable files. Next, we will introduce the use of executable files in detail.

When running the executable file, you need to prepare the following resources:

--url "https://* * * " The address of the LLM to be called

--key " * * * " --llm "gpt-4o" The API key to call LLM

Enter the project directory:

```cd /BTBOT```


## demo

For the automatic charging task in the paper, you can use the following command to view the running results of BTBOT.

`./dist/main_pre_check_change --task "demo" --url "https://* * *" --key "* * *" --llm "gpt-4o" --data-path "/BTBOT/data"`

In this example, the output is:

**['?', ['>', 'lowBattery', ['?', 'atCharge', 'goToCharge'], 'charging'], 'doOtherTask']**

The graphical representation of the behavior tree program is shown below.

<img src="https://github.com/BTBOT-src/BTBOT/blob/main/BT1.png" alt="btbot" width="300">



In addition, if you want to try to solve other tasks, such as: ***charge, ballFound, doTask, findfood, firefighting***, please modify the task field in the command to solve the corresponding task.

### BTBOT effect

### benchmark

The benchmark used in this work contains 70 tasks with different difficulties and scenarios. Please use the following command to view the distribution of the benchmark.

```python box2.py```

The detailed data for the 70 tasks in the benchmark are shown below.

The detailed data for the 70 tasks in the benchmark are shown in benchmark.pdf.

The program execution will get a benchmark.pdf file, which stores an image and shows the complexity of the nodes contained in the task in the form of a box plot. Its horizontal axis represents four scenarios, Movement (tasks related to movement), Transmission (tasks related to delivering items), Manipulation (tasks related to robot arm operation), Priority (tasks related to the robot's environment that requires decision-making)


### BTBOT robustness to different LLMs

In this work, the impact of different performance LLMs on BTBOT is discussed. Execute the following instructions to view the impact of different LLMs on BTBOT and compare them with the effect of generating BT programs with LLM. Among them, the files that the executable file depends on are located in the BTBOT/data directory.

```./dist/main_LLM3 --result "result" --url "https://* * *" --key "* * *" --llm "gpt" --data-path "/BTBOT/data" >> BTBOT_BTLLMGen.txt```

The output of the executable file is redirected to BTBOT_BTLLMGen.txt. The file stores the detailed results of BTBOT using three different LLMs to solve the task and the results of LLM solving the task, as well as a piece of latex code. The latex code compares the effects of BTBOT and BTLLMGen on different LLMs, the number of completed tasks, and the success rate.


## baseline

### Comparison with fine-tuning LLM baseline

First, we compare with the existing LLM fine-tuning technology BTGenBot. On the test set of BTGenBot, we use BTBOT to solve these tasks. You can view the output results of BTBOT on the test set through the following command.

```./dist/main_BTGENBOT --result "result" --url "https://* * *" --key "* * *" --llm "gpt-4o" --data-path "/BTBOT/data" >> BTBOT_BTGenBot.txt```

The executable file output results are redirected to BTBOT_BTGenBot.txt. The file stores BTBOT's solution to the test tasks (9 test tasks) used in the BTGenBot work, as well as a latex code for statistical analysis and comparison of the two works. Among them, the successfully solved tasks are represented by **√**.

<img src="https://github.com/BTBOT-src/BTBOT/blob/main/btgenbot.png" alt="baseline" width="450">


### Comparison with other BT generation baselines

In addition, we also compare with the existing work that generates BT using Monte Carlo tree search technology (MCTS-Syn) and the baseline that directly generates BT using LLM (GPT-4o-Syn). Use the following command to view the latex code corresponding to the experiment operation and results.

```./dist/baseline --result "result" --url "https://* * *" --key "* * *" --llm "gpt-4o" --data-path "/BTBOT/data" >> baseline.txt```

The executable file output result is redirected to baseline.txt. Similarly, a section of latex code is output to statistically analyze the performance of multiple baselines on the benchmark. This section of latex generates a picture, in which the horizontal axis represents the time required to solve a task. The vertical axis represents how many tasks can be solved within a given time. Compare the performance of BTBOT and baselin work from the perspectives of efficiency and success rate.

<img src="https://github.com/BTBOT-src/BTBOT/blob/main/baseline.png" alt="btgenbot" width="400">




## Ablation Study

In this work, we proposed three key technologies, which resulted in five BTBOT variants (NoPattern, NoPrune, NoControlRepair, NoStructureRepair, NoRepair). You can view the running results and effect display by executing the following command.

```./dist/ablation --result "result" --url "https://* * *" --key "* * *" --llm "gpt-4o" --data-path "/BTBOT/data" >> ablation.txt```

In the output file, the executable file outputs the solution of each variant (including BTBOT) to the benchmark, and the statistical results are output as the file Figure13:Ablation_study_of_BTBOT.png.

<img src="https://github.com/BTBOT-src/BTBOT/blob/main/ablation.png" alt="ablation" width="400">

## User Study

We recruited 12 professional and non-professional behavior tree users to conduct user testing by handwriting target behavior trees and using BTBOT to generate behavior trees. The results are stored in the /BTBOT/data/userstudy.zip directory. The results of the user test are shown in the figure below. As can be seen from the figure, BTBOT is very helpful in helping users generate the desired BT.

<img src="https://github.com/BTBOT-src/BTBOT/blob/main/userstudy.png" alt="userstudy" width="400">






