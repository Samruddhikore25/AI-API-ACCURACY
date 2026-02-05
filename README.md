AI API ACCURACY 

Abstract

This project focuses on comparison of two large LLM models: Gemini and Cohere. Each model is evaluated on 387 mathematical problems of different domains and difficulty levels.
The comparison examined the accuracy, responsiveness and quality of response of both the models. Cohere attempted to answer all the questions but with a lower accuracy of 28.42%.Gemini failed to answer 153 questions due to timeouts and achieved an accuracy of 32.91%. 
Both models strived with algebra and multi-step reasoning. Overall, the results showed that even advanced large language models are still struggling to achieve accuracy, numeric reasoning and error handling.

INTRODUCTION

Large language models (LLMs) have remarkably seen a spike in their popularity due to their capabilities. Despite this significant growth, LLMs are struggling to achieve precision and alignment in the field of mathematical problems.
Different architectures produce different outputs based on their capabilities. Unlike natural language tasks, mathematical tasks require precision, adherence to symbolic parameters, and strict compliance with task instructions.
This study evaluates two prominent LLMs: Gemini and Cohere on a specific set of mathematical questions. Based on the observations collected by comparing models on 387 questions, the research aims to provide factual strengths and limitations of these models for every sector 
that involves mathematical computing.

RESEARCH METHODOLOGY 

1.	Dataset: MathOdyssey: Benchmarking Mathematical Problem-Solving Skills in Large Language Models Using Odyssey Math Data
   
A total of 387 mathematics questions were used. They encompassed a wide variety of topics including:
1. Algebra                                       5. Geometry                                   9. Probability 
2. Calculus                                     6. Linear Algebra                          10. Series
3. Combinatorics                            7. Pre-Calculus                             11. Trigonometry
4. Differential questions                 8. Statistics

•	Difficulty levels were annotated as:
1.	High school math    
2.	High school competition  
3.	College math
2. Model Selection and Configuration

Two distinct, high-performance LLMs were selected for comparison:
•	Cohere Model: command-a-03-2025
•	Google Model: gemini-2.5-flash-lite

All 387 questions were sent one at a time to each model. We also used a strict system message to see whether the models could follow the required format.
System Message: "Give only the exact numeric answer in less than 5 words. No words. No steps."
The temperature and Top-P settings for both API calls were set to their defaults to prioritize deterministic output.

3. Evaluation Criteria
Models were evaluated on:
1.	Overall accuracy
2.	Accuracy by mathematical topic
3.	Accuracy by difficulty level
4.	Responsiveness (successful vs. skipped responses)
5.	Qualitative analysis of mistakes


4. Data Processing

•	Raw answers were saved as JSON, converted to CSV, and manually cleaned when models:
1. Returned full explanations instead of answers
2. Returned multiple options
3. Returned numerical values without selecting A/B/C/D
4. Gave answers not present in the options

•	Only one corrected option per question was used for accuracy scoring.



EMPIRICAL RESULTS & ANALYSIS 

1.	Response Rate and Completeness
The striking observation of this analysis is the response coverage:
METRIC	COHERE	GEMINI
Total Questions	387	387
Questions Answered	387	234
Questions Skipped	0	153
Skip Reason	-	API Timeout(30s)
This suggests that Cohere’s has superior robustness in terms of quantitative API requests,constantly providing outputs even though the problem is out of its capability.Thus Cohere can be trusted when there is a critical requirement of guaranteed answer.
Cohere gave faster replies than Gemini.

3.	Overall Accuracy
MODEL	ACCURACY	 QUESTIONS
Cohere	28.42%	384
Gemini	32.91%	384


4.	Accuracy By Label & Difficulty Level
I] Cohere’s Accuracy by Label & Difficulty Level:


II] Gemini’s Accuracy by Label & Difficulty Level

 

OBSERVATIONS:
 General Observations
1.	Cohere produces faster responses than Gemini.
2.	All 387 questions were sent as individual API calls.
3.	Cohere answered all 387 while Gemini answered 234, skipping 153 due to continuous timeout errors.
4.	Every new run on AncientBrain website compares 10 randomly selected questions.
5.	Outputs were initially stored in JSON and converted to CSV for scoring procedures.
6.	Both models frequently failed to select exactly one choice between A to D, requiring manual correction.
7.	Despite obvious instructions provided only short numeric answer, both models gave lengthy explanations that had to be cut down.
8.	Both models gave poor performance on Algebra questions often producing incorrect or partially correct solutions.
9.	Jupyter Notebook was employed for calculating overall accuracy and generating visualizations.


Cohere-Specific Observations
1.	Provided near correct solutions (e.g. Q212, Q324, Q377) but often missed final precision.
2.	Misinterpreted numerical outputs as option labels (e.g. interpreting “1” as A, “3” as C in Q238).
3.	Sometimes produced answers not present among the options (Q227).
4.	Returned correct numeric values but failed to choose an option (multiple items).
5.	Produced partially correct answers (Q233, Q242, Q266).
6.	Selected multiple choices instead of one (Q237).
7.	Made errors on simple calculations, such as matrix determinant (Q288).
8.	Mixed performance in statistical questions: correct mean but incorrect standard deviation and confidence interval components (Q376).


Gemini-Specific Observations
1.	Occasionally produced near-correct or insightful responses (e.g., chess problem Q113; Q284).
2.	Matched Cohere’s wrong answers in some cases (Q136, Q276).
3.	Generated partially correct results (Q201).
4.	Returned numeric values intended to correspond to options (e.g., answering “4” to indicate option D in Q220).
5.	Correctly solved part of vector/matrix problems but failed subsequent steps (Q302).
6.	Computed some parameters correctly (e.g., α) but failed others (e.g., β in Q328).
7.	Failed to respond to 153 questions due to repeated request timeouts:
HTTPSConnectionPool(host="generativelanguage.googleapis.com"): Read timed out (30s).


CONCLUSION

This empirical evaluation demonstrates that both Cohere and Gemini still face substantial challenges in mathematical reasoning, precision, and instruction adherence. While Gemini achieved higher accuracy on the subset of questions it answered, 
Cohere’s consistent responsiveness makes it more reliable for large-scale automated workflows. Future work should focus on improving math reasoning, handling complex problems consistently, and following strict instructions to make LLMs more reliable for quantitative tasks.

REFERENCES 
[1] MathOdyssey: Benchmarking Mathematical Problem-Solving Skills in Large Language Models         
Using Odyssey Math Data (https://arxiv.org/abs/2406.18321) 
