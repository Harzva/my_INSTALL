```
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: 当前文件",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal"
        },
        {
            "name": "train.py",
            "type": "python",
            "request": "launch",
            "program": "/mnt/4T/hzh/TransFG/train.py",
            "console": "integratedTerminal",
            "args": ["--dataset","coco",
                 "--net" ,"res50" ,
                "--bs" ,"4", "--nw" ,"4" ,
                "--cuda","True" ,"--g","1", "--seen" ,"1","--mGPUs" ,"True"],
            "env": {"CUDA_VISIBLE_DEVICES":"2,3"},  
            "justMyCode": false
        }, 
        {
            "name": "train_lanch.py",
            "type": "python",
            "request": "launch",
            "program": "/home/ubuntu/.conda/envs/hzh36/lib/python3.6/site-packages/torch/distributed/launch.py",//可执行文件路径
            "console": "integratedTerminal",
            "args": [
                "--nproc_per_node=4",
                "/mnt/4T/hzh/TransFG/train.py",
                "--dataset","CUB_200_2011","--split","non-overlap","--num_steps","10000","--fp16","--decay_type", "cosine" ,"--model_type" ,"ViT-B_16_2",
            ],
            "env": {"CUDA_VISIBLE_DEVICES":"0,1,2,3"},
        }

    ]
}




https://code.visualstudio.com/docs/python/debugging
https://www.freesion.com/article/55341206024/
https://dalewushuang.blog.csdn.net/article/details/107705492?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1.no_search_link&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1.no_search_link&utm_relevant_index=2
```



```

    {
        "name": "demo",
        "type": "python",
        "request": "launch",
        "program": "/home/ubuntu/Dataset/Partition1/dyy/IPIU-VAD-dyy/demo.py",
        "console": "integratedTerminal",
        "justMyCode": true,
        "cwd":"${fileDirname}"

    }
sys.path.append(".")
```
code runner
1
"python": "python",


2
当前文件夹作为目录 
"python": "cd $dir \n python -u $fileName",

 "code-runner.executorMap": {
       "python": "cd $dir \n conda activate py36 \n python -u $fileName",


手动打开就可以哪就是工作目录

最终两种运行模式
一种coderun 当前文件为工作目录
另外一种就是当前终端路径为工作目录

而debug
cwd 就可以



 "code-runner.fileDirectoryAsCwd": true,
Terminal Here
Terminal All In One