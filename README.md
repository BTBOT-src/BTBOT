# BTBOTWe have put the code and executable files of BTBOT on the docker hub website. You only need to get the docker image by following the instructions below.

`docker pull btbot123/btbot`

We package the project into an executable file. You only need to execute the corresponding instructions to output the task and its corresponding behavior tree program in the console.

Before executing the executable file, you need to prepare the following information:

Call the URL corresponding to LLM, your API key.

The following will show the execution results of BTBOT by solving the demo example task.

For example, by executing the following command, solve the **demo** task (automatic charging task, consistent with the paper)

`cd /BTBOT`

`./dist/main_pre_check_change --task "demo" --url "https://* * *" --key "* * *" --llm "gpt-4o"`

Enter the address of LLM in the url field, for example, you use the openAI API to call ChatGPT.

Enter the API key in the key field.
Finally, the llm field corresponds to the model that calls LLM. You can switch to other models such as gpt-4o, gpt-3.5-turbo, gpt-4-turbo, etc.

The task field corresponds to the task name of the task to be solved. To solve other tasks, you only need to modify the content of the task field. For example, "charge", "demo", "doTask", "get_food", all tasks are recorded in the benchmar.xlsx file.

At the same time, we provide the following scripts and executable files to show the corresponding output effects on the 70 tasks of the benchmark. The output content is: task name task corresponding BT.

`cd /BTBOT`

`./dist/(A exe file) --task "demo" --url "https://* * *" --key "* * *" --llm "gpt-4o"`

Among them, please replace the content of A exe file with a specific executable file:

main: BTBOT's executable file in the benchmark. **BTBOT**

main_LLMgen: corresponds to the process of directly using LLM to generate BT in the baseline in the paper. **GPT-4o-BT/BTLLMGen**

main_noPrune: corresponds to the process of not using pruning technology in the ablation experiment section in the paper. **NoPrune**

main_noPattern: corresponds to the process of not using language patterns in the ablation experiment section in the paper. **NoPattern**

main_noModifyNodes: corresponds to the process of not using modification control nodes for repair in the ablation experiment section in the paper. **NoControlRepair**

main_noExpandSketch: corresponds to the process of not using extended behavior tree structure for repair in the ablation experiment section in the paper. **NoStructureRepaire**

main_noRepair: corresponds to the process of not using any sketch repair technology in the ablation experiment section in the paper. **NoRepair**

At the same time, execute the following instructions to show the results of MCTS-Syn technology on the benchmark.

`cd /BTBOT/benchmark/baseline/BehaviorTree-Synthesis/BT_Synthesis/src`

`bash script.sh`



Thank you very much for your interest in our work. Please contact me if you have any questions.
