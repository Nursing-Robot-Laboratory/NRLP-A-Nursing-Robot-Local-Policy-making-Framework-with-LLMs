# ReadMe for NRLP

1. ### Environment

   python 3.11

   Mujoco 2.3.7 [here](https://github.com/google-deepmind/mujoco/releases/download/2.3.7/mujoco-2.3.7-windows-x86_64.zip)

2. ### Nursing Robot with Local Policy-making

   2.1 execute_dispatch.py launches Inference, including the teacher model's inference in data amplification, the distilled local model's inference in iterative training and the inference for controlling the robot.

   2.2 The generated LLM plan follow the structure in plan_structure_LLM.py. To transform the Text-based LLM plan to this structure, a parser in parser.py is employed.

   2.3 The actuator.py transform the format LLM plan to a goal configuration with format in pathplan_structure.py for all robot joints. The robot and env are build by robot.py and base_env.py

   Program Run: python execute_dispatch.py --env="Environment" --data_dir="data" -- run_name="test" --run_num=1 --max_steps=10 --debug_mode=False llm_model="adapter_model" --max_tokens=300

3. ### Finetune

   finetune.py perform SFT for local LLM model. Our finetune parameters are also in this file. The backbone model can be download in [here](https://huggingface.co/meta-llama/Llama-3.2-11B-Vision). The finetuned tensors are stored in adapter_model.safetensors. The train samples and test samples are stored as PKL file, and our run result are stored  in include_answer_test.pkl.

   Due to the limitation of uploading size, GitHub only shows part of the representative results, and  the complete experimental results and videos can be obtained from the following web disk: 

   https://pan.baidu.com/s/1IyveDvAf28itfg6JeIvDpQ

   Key: g7eh

4. ### Implementation on Real Robot

   Realize the transfer of robot trajectory from Mujoco to dual arm nursing robot.

   Program Run: Sim-to-Real.py

Please feel free to change and use the code for review and academic purposes. If you have any  questions, please contact us by: jxxie20@fudan.edu.cn
