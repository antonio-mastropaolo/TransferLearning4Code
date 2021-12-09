# Using Transfer Learning to support Code-Related tasks

In this study, we extend our previous work <a href='https://ieeexplore.ieee.org/abstract/document/9401982/'>**Studying the usage of text-to-text transfer transformer for code-related tasks**</a> paying particular attention at the role played by pre-training and multi-task fine-tuning on the model's performance.


#### Pipeline

In order to pre-train and then finetune a [T5 small](https://github.com/google-research/text-to-text-transfer-transformer) model, we need a new sentencepiece model to accommodate the expanded vocabulary given by the java programming language, abstracted java tokens, and technical natural language.



*  ##### How to train a new <a href='https://github.com/google/sentencepiece/blob/master/python/README.md'>SPmodel</a>

    *Pythonic way*

    ```
    pip install sentencepiece
    import sentencepiece as spm
    spm.SentencePieceTrainer.train('--input=pretraining.txt --model_prefix=dl4se --vocab_size=32000 --bos_id=-1  --eos_id=1 --unk_id=2 --pad_id=0') 
    ```
    The new SPmodel has to be trained on the entire pre-training corpus.

* ##### Set up a GCS Bucket
    To Set up a new GCS Bucket for training and fine-tuning a T5 Model, please follow the orignal guide provided by <a href='https://www.google.com'> Google </a>. 
    Here the link: https://cloud.google.com/storage/docs/quickstart-console
    Subsequently, by following the jupyter notebook we provide for pre-train and fine-tune the network, you should be able to set up the final environment.

* ##### About the datasets

    The datasets for the pre-training and the fine-tuning can be found
    <a href="https://drive.google.com/drive/folders/1AN9tc6rSmSNX2AqgAkTNyqW4ozCuhN9u?usp=sharing">here</a>


* ##### Pre-trainig/Fine-tuning 
  
    To pre-train and then, fine-tune T5, please use the script we provide here:
    - <a href ='https://github.com/antonio-mastropaolo/T5-learning-ICSE_2021/blob/main/Code/pre-training.ipynb'>Pre-Training</a> 
    -  <a href ='https://github.com/antonio-mastropaolo/T5-learning-ICSE_2021/blob/main/Code/fine-tuning.ipynb'>Fine-Tuning</a> 

* ##### How to generate the predictions

    First you need to convert the TF model into a pytorch model by using <a href='https://github.com/antonio-mastropaolo/T5-learning-ICSE_2021/blob/main/Code/Miscellaneous/tf_2_pytorch_T5.py'> TF_to_Pytorch </a>, then run <a href='https://github.com/antonio-mastropaolo/T5-learning-ICSE_2021/blob/main/Code/run-on-test-set/generate_results.ipynb'> Generate Results </a>

* ##### Our results: https://drive.google.com/drive/folders/14ywfhJorNNeWxgSV1bI0XIzlLAFu8odH?usp=sharing


**Additional:** In <a href='https://github.com/antonio-mastropaolo/T5-learning-ICSE_2021/tree/main/Code/Miscellaneous'>Miscellaneous</a> folder, you can find all the additional scripts we used for computing the BLEU score and the overlap metrics. Furthermore, <a href='https://drive.google.com/drive/folders/1caP5-OpurKOMhkqfsrkHxKarEoYVjiFI?usp=sharing'>here</a> and <a href='https://drive.google.com/drive/folders/1A5tjYfpYr7rlf_A2FqGB-XLEcFOFYDfB?usp=sharing'>here</a> you can also experiment with our pre-trained and fine-tuned models.



* ##### Models
  * <a href="https://drive.google.com/drive/folders/1vqNozabCLoAgIG8qJJ6qs0W8s77-FrPc?usp=sharing">No Pre-Training</a>
  * <a href="https://drive.google.com/drive/folders/15Wx9dBlqQxV1zFeHl_uh2JoRBZ9oPt4l?usp=sharing">Pre-Training Single Task</a>
  * <a href="https://drive.google.com/drive/folders/1CU_rS-BX9BchUhQEbis4CYH2w6syJ6i2?usp=sharing">Pre-Training Multi Task (Proportional Sampling)</a>
  * <a href="https://drive.google.com/drive/folders/1SjIdfQUDPH5NI5KseHypkln0yiYN8-Jr?usp=sharing">Pre-Training Multi Task (Balanced Sampling)</a>
  
<!-- * ##### Results:  :open_file_folder: 
    * <a href='https://drive.google.com/drive/folders/1Kutaau3q5vPP3phaWtdmouZ5bvHHipwM?usp=sharing'>Multi-Task</a>
    * <a href="https://drive.google.com/drive/folders/1cPJElLO_C1MoPp0dWAlmPX77CMNW0SAP?usp=sharing">LogSTMT only Task</a>
    * <a href="https://drive.google.com/drive/folders/1Ea4WxrdxD4nPOeOLsoSonM7NYqKe-Snn?usp=sharing">Denoising only Task</a>
    * <a href="https://drive.google.com/drive/folders/1FRERpcgcEdG6b7Cp4WpURbZR3TGtGa6I?usp=sharing">No Pre-trained</a> -->


* ##### Additional:
    Under <a href='https://drive.google.com/drive/folders/1K9RNuQBgyoCSenZz0ioNiD5YP9E1pf2S?usp=sharing'>Miscellaneous</a>, you can find the additional script used for computing the statistical tests, the complementary analysis and the bleu score.





    


