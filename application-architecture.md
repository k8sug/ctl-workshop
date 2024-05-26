# Application Architecture

##

##

##

##

## GODEL - LLM MODEL

<figure><img src=".gitbook/assets/image (19).png" alt=""><figcaption><p>GODEL (<strong>G</strong>rounded <strong>O</strong>pen <strong>D</strong>ialogu<strong>e</strong> <strong>L</strong>anguage Model), a large <strong>open-source</strong> pre-trained language model for dialog. </p></figcaption></figure>

<figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

It is parameterized with a Transformer-based encoder-decoder model and trained for response generation grounded in external text, which allows more effective fine-tuning on dialog tasks that require conditioning the response on information that is external to the current conversation (e.g., a retrieved document). The pre-trained model can be efficiently fine-tuned and adapted to accomplish a new dialog task with a handful of task-specific dialogs.

> @misc{\
> peng2022godel, \
> author = {Peng, Baolin and Galley, Michel and He, Pengcheng and Brockett, Chris and Liden, Lars and Nouri, Elnaz and Yu, Zhou and Dolan, Bill and Gao, Jianfeng}, \
> title = {GODEL: Large-Scale Pre-training for Goal-Directed Dialog}, \
> howpublished = {arXiv}, \
> year = {2022}, month = {June}, \
> url = {https://www.microsoft.com/en-us/research/publication/godel-large-scale-pre-training-for-goal-directed-dialog/}, }
