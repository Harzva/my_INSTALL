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


