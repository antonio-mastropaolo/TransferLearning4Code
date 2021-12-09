# Using Transfer Learning for Code-Related Tasks

In this study, we extend our previous work <a href='https://ieeexplore.ieee.org/abstract/document/9401982/'>**Studying the usage of text-to-text transfer transformer for code-related tasks**</a> paying particular attention at the role played by pre-training and multi-task fine-tuning on the model's performance.


#### Pipeline

In order to pre-train and then finetune a [T5 small](https://github.com/google-research/text-to-text-transfer-transformer) model, we need a new sentencepiece model to accommodate the expanded vocabulary given by the java programming language, abstracted java tokens, and technical natural language.



*  ##### How to train a new <a href='https://github.com/google/sentencepiece/blob/master/python/README.md'>SPmodel</a>

    *Pythonic way*

    ```
    pip install sentencepiece==0.1.96
    import sentencepiece as spm
    spm.SentencePieceTrainer.train('--input=pretraining.txt --model_prefix=dl4se --vocab_size=32000 --bos_id=-1  --eos_id=1 --unk_id=2 --pad_id=0') 
    ```
    The new SPmodel has to be trained on the entire pre-training corpus.
    The tokenizer we trained is available <a href="https://drive.google.com/drive/folders/1-ihXMwst4GL6yuFYV3DZl_E1yWmoEdE8?usp=sharing">here</a>

* ##### Set up a GCS Bucket :bulb:
    To Set up a new GCS Bucket for training and fine-tuning a T5 Model, please follow the orignal guide provided by <a href='https://www.google.com'> Google </a>. 
    Here the link: https://cloud.google.com/storage/docs/quickstart-console
    Subsequently, by following the jupyter notebook we provide for pre-train and fine-tune the network, you should be able to set up the final environment.

* ##### Datasets :paperclip:

    The datasets for the pre-training and the fine-tuning can be found
    <a href="https://drive.google.com/drive/folders/1AN9tc6rSmSNX2AqgAkTNyqW4ozCuhN9u?usp=sharing">here</a>


* ##### Pre-trainig/Fine-tuning :computer:
    To pre-train and then, fine-tune T5, please use the script we provide here:
    - <a href ='https://github.com/antonio-mastropaolo/TransferLearning4Code/blob/main/Code/Pre-Training/Pre-Training.ipynb'>Pre-Training</a> 
    -  <a href ='https://github.com/antonio-mastropaolo/TransferLearning4Code/blob/main/Code/Fine-Tuning/Fine-Tuning.ipynb'>Fine-Tuning</a> 

* ##### How to generate the predictions :chart_with_upwards_trend:
    First you need to convert the TF model into a pytorch model by using <a href='https://github.com/antonio-mastropaolo/T5-learning-ICSE_2021/blob/main/Code/Miscellaneous/tf_2_pytorch_T5.py'> TF_to_Pytorch </a>, then run <a href='https://github.com/antonio-mastropaolo/TransferLearning4Code/blob/main/Code/Run-on-test/Generate-Result.ipynb'> Generate Results </a>


* ##### Models :bar_chart:
    * <a href="https://drive.google.com/drive/folders/1CRE809bsalIJRcdzd770pq5kSUiIr0jj?usp=sharing">No Pre-Training</a>
    * <a href="https://drive.google.com/drive/folders/1R23fXWC8YPz3SgLDp-BxcLXAQ1exh4Vh?usp=sharing">Pre-Training Single Task</a>
    * <a href="https://drive.google.com/drive/folders/15j7vlWKL3F40ac2acU2AxjFbAXnNKLjF?usp=sharing">Pre-Training Multi Task (Proportional Sampling)</a>
    * <a href="https://drive.google.com/drive/folders/1Jnh-3z2vm3r4t8RcofenvFXjT95V4ORJ?usp=sharing">Pre-Training Multi Task (Balanced Sampling)</a>
  
* ##### Predictions:  :open_file_folder:  <a href="https://drive.google.com/drive/folders/1jXiYiqjc78QLz8si1KBTp6DfRmwmNzhz?usp=sharing"> Click Me! </a> 

* ##### Additional: :clipboard:
    Under <a href='https://drive.google.com/drive/folders/1K9RNuQBgyoCSenZz0ioNiD5YP9E1pf2S?usp=sharing'>Miscellaneous</a>, you can find the additional script used for computing the statistical tests, the complementary analysis, the overlap and data snooping analysis.


* ##### Extra: :clipboard:
    * Hyperparameters tuning results are available <a href="https://docs.google.com/spreadsheets/d/1rPpaRXOe3NOMXFMaedRgq8juON-S6g6jF6AiNA_0vxw/edit?usp=sharing"> here </a>
    * To navigate the replication package click <a href="https://drive.google.com/drive/folders/1-9q0a0oyvMGlaaz1UJNlu9r6dG6BH2YK?usp=sharing">here</a> 

    

