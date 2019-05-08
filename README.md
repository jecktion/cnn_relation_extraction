## 基于卷积深度神经网络的关系分类


TensorFlow实现[论文]（http://www.aclweb.org/anthology/C14-1220），

于@FrankWork原始代码:https://github.com/FrankWork/conv_relation

csdn: https://blog.csdn.net/weixin_41779045/article/details/89948143

数据集：SemEval2010 task8

单词嵌入：senna

运行代码：
```
./run
```

## 环境（已测试）
- tensorflow 1.4.0
- python 3.5
- linux,macOs or windows

## 如何运行 ?

- 训练模型

    `./run`
    
    where ```num_epochs=200 --word_dim=50```have been set in 'run' file.
-  测试模型
 
    执行 

    `python src/train.py  --num_epochs=200 --word_dim=50 --test`

	然后你可以得到一个 'results.txt' 文件 /data/resuts.txt```

- 计算F1得分

    ```perl src/scorer.pl data/test_keys.txt data/results.txt```



##  问题:
如果您使用Spyder或PyCharm来运行此代码，您可能会遇到此错误：


```
ArgumentError: argument --train_file: conflicting option string: --train_file
```

solution:

1. restart spyder

2. or add annotation for all definitions of ```tf.flags.FLAGS``` .

such as ```# flags.DEFINE_string("train_file", "data/train.cln", 
                             "original training file")```

## 区别:


1.删​​除'隐藏层2'作为[提到的论文]（http://www.aclweb.org/anthology/C14-1220）   
2.在卷积层中使用多窗口大小（w = 3，w = 4，w = 5）  
3.删除Wordnet词法功能


## 最终评估
emEval 2010任务8有最终评估，运行和最终f1分数的书面记分员将被写入 results_scores.txt

```perl src/scorer.pl data/test_keys.txt data/results.txt```
Done training, best_step: 12960, best_acc: 0.7751   
duration: 0.20 hours  
accuracy: 0.7751




