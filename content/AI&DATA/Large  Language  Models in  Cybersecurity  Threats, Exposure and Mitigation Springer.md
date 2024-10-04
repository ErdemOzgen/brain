


Such a trade-off is known as scaling laws—an optimal relationship between the  model size, dataset size, and computational power investment required to achieve  the best model performance while minimizing computational expenses. There are  currently two schools of thought on what this scaling law is. 

[[Chinchilla scaling law]]

Perhaps the most known example is the so-called “[[Chain-of-thought]]” prompting,  published in early 2022 . The trick in that technique is to prime the generation of  more high-quality reasoning-like utterances by providing an example of a solution  to a reasoning problem that makes all steps explicit rather than directly outputting  the answer, allowing the attention maps to better identify and articulate in a more  plausible manner predicates involved in reasoning. Shortly after, an even more  powerful, zero-shot approach was identified when a prompt requesting reasoning  was terminated with a “let us reason step-by-step”, restraining the generation  space to educational examples of reasoning present in the training dataset, at which  point their structure allowed the attention maps to operate in the case similar to the  few-shot approach previously presented. 

