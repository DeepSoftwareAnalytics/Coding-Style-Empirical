# Beyond Functional Correctness: Examining Inconsistencies in Coding Styles of LLM-based Code Generation

## 📦RQ1(Please see RQ1_temp)
### 📄Code samples generated by LLMs 
(Please see **RQ1_temp/code_samples_generated_by_LLMs**) 
> For each of the 230 Python code generation tasks from **CoderEval**, we prompt the five LLMs (**CodeLlama-7B**, **StarCoder2-7B**, **DeepSeekCoder-1.3B**, **DeepSeekCoder-6.7B**, and **GPT-4**) to perform code generation using the same prompting template (function signature and docstring). For each task, we instruct each model to generate 10 results, resulting in an initial total of **2,300 code samples** for each model. To ensure the correctness of the collected code samples, we further filter out code samples that fail to pass any of the associated unit tests for the task, leading to **456**, **189**, **365**, **497**, and **570** results that pass all tests for CodeLlama-7B, StarCoder2-7B, DeepSeekCoder-1.3B, DeepSeekCoder-6.7B, and GPT-4, respectively.

### 📄1179 unique code samples
(Please see **RQ1_temp**) 
> We further merge identical code samples to reduce analysis effort, resulting in 1,557 unique samples. We only annotate 1,557 unique code samples to ensure that the annotation results for the same code sample generated by different models are consistent, thereby avoiding the situation where the same code sample generated by different LLMs is annotated with different results. We filter out results that exhibit no inconsistency in coding style. As a result, 73 code samples are filtered out in this way(see **Manual_filtering/Style_consistency.xlsx**). We filter out results that implement the task incorrectly despite passing the unit tests. The functional correctness of the generated result is verified by comparing it to the ground truth and the task descriptions. Previous work has shown that existing benchmarks suffer from test sufficiency issues, meaning that even if a generated result passes all tests, there is still a chance it could be incorrect. As a result, 286 code samples are filtered out in this way(see **Manual_filtering/Functional_correctness.xlsx**). We filter out results that contain extra code that does not contribute to fulfilling the function’s implementation requirements (e.g., two exactly the same loops). As a result, 19 code samples are filtered out in this way(see **Manual_filtering/Implementation_conciseness.xlsx**). Finally, we obtain **1,179** unique code samples for the study.
> The **1179_unique_samples** file has been split into five tables:

- **Part 1:** `1179_unique_samples_part1.xlsx`
- **Part 2:** `1179_unique_samples_part2.xlsx`
- **Part 3:** `1179_unique_samples_part3.xlsx`
- **Part 4:** `1179_unique_samples_part4.xlsx`
- **Part 5:** `1179_unique_samples_part5.xlsx`

### 📄Rewritten ground truths
(Please see **RQ1_temp/rewritten_ground_truths.xlsx**) 
> Since each task in CoderEval has one ground truth, and a single ground truth can only reflect the coding style of one programmer, we addressed this issue by randomly selecting 42 Python tasks from the 230 available in CoderEval. Two annotators were assigned to independently rewrite the ground truths for these 42 tasks, resulting in a total of **84** ground truths. Another annotator was responsible for verifying the correctness of these ground truths.

### 📄Comparing results with rewritten groud truths
(Please see **RQ1_temp**) 
> We then identified the code samples corresponding to these 42 tasks from a set of 1,179 unique code samples and annotated the coding style differences between the rewritten ground truths and the code samples following the outlined annotation process. After the annotation process, the overall taxonomy remained unchanged.

### 📄Java_code_samples
(Please see **RQ1_temp/DeepSeekCoder_6.7B_java_samples.xlsx**) 
> We used DeepSeekCoder-6.7B to execute 230 Java tasks in CoderEval, generating 10 code samples for each task, resulting in a total of 2,300 code samples. Among them, 604 code samples passed all test cases for each task. We further merged identical code samples to reduce the analysis effort, resulting in 396 unique samples. We filter out results that exhibit no inconsistency in coding style. As a result, 64 code samples are filtered out in this way. We filter out results that implement the task incorrectly despite passing the unit tests. As a result, 12 code samples are filtered out in this way. We filter out results that contain extra code that does not contribute to fulfilling the function’s implementation requirements. As a result, 1 code samples are filtered out in this way. Finally, we annotated the remaining **319** Java code samples.


## 📦RQ2(Please see RQ2_temp)
### 📄Models_code_samples
(Please see **RQ2_temp**)  
> Here are the code samples used in section 4.2.2-4.2.3 generated by five models. These code samples are functionally correct, without extra code, exhibiting differences with ground truths in code style. The code samples have not undergone deduplication.


## 📦RQ3(Please see RQ3_temp)
### 📄Coding style comparison
(Please see **RQ3_temp**) 
> We compare the code samples generated by LLMs from RQ1 with their corresponding ground truths and evaluate each of the three aspects. For each analysis, we determine whether the generated code is better than the ground truth ("model better"), whether they are comparable ("tie"), or whether the ground truth is better ("human better"). In the table, "**-1**" represents "**model better**", "**0**" represents "**tie**", and "**1**" represents "**human better**".


## 📦RQ4(Please see RQ4_temp)
> We conduct experiments with DeepSeekCoder-6.7B on 20 sampled Python tasks from CoderEval. We choose DeepSeekCoder-6.7B to conduct the experiment. These tasks are randomly selected from those that DeepSeekCoder-6.7B can complete, meaning DeepSeekCoder-6.7B can generate code samples that pass all corresponding test cases. We design four types of enhanced prompts for this study, aiming to instruct the model to generate code with better coding style using explicit style guidelines. The design of these prompts investigates the impact of the placement and detail level of style guidelines. In prompt names, “-head” or “-end” specifies whether the style guidelines are placed before the function signature and docstring, similar to a directive, or appended at the end of the original docstring, simulating a normal docstring style. “-concise” and “-detailed” indicate the level of detail in the style guidelines. The detailed version includes three specific principles related to code readability, conciseness, and robustness, in addition to the concise information. According to the scoring principles outlined in Section 4.3, we evaluated the code samples generated using the basic prompt and four enhanced prompts for readability, conciseness, and robustness. 

### 📄The scoring results of basic prompt
(Please see **RQ4_temp/scoring_results_basic_prompt.xlsx**) 
> The results from the two annotators mentioned in Section 4.3 were based on the scoring principles outlined in the same section, where they evaluated the code samples generated from **basic prompt** for readability, conciseness, and robustness.

### 📄The scoring results of four enhanced prompts
(Please see **RQ4_temp/scoring_results_enhanced_prompts.xlsx**) 
> The results from the two annotators mentioned in Section 4.3 were based on the scoring principles outlined in the same section, where they evaluated the code samples generated from **four enhanced prompts** for readability, conciseness, and robustness. The results for Prompt-1, Prompt-2, Prompt-3, and Prompt-4 correspond to the scoring outcomes of Prompt-head-concise, Prompt-head-detailed, Prompt-end-concise, and Prompt-end-detailed, respectively.
![Prompt templates](https://github.com/DeepSoftwareAnalytics/Coding-Style-Empirical/blob/main/images/prompts-4.png)
