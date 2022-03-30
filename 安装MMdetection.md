# step 0: 检查系统环境

```python
""" 主要看是否安装anaconda、以及cuda版本 """
#　检查conda，命令行输入conda即可
conda 
# 如果没报错，就进行下一步，否则安装conda环境

#　检查cuda版本
ls /usr/local
# 输出目录有cuda-**.* (**.*)就是cuda的版本
```

# step 1: 创建conda虚拟环境，安装pytorch

```Python
""" 创建虚拟环境是为了包的管理, 做一个尝试一般都需要新建一个虚拟环境，防止污染已有环境"""
# 查看已有环境
conda info --envs

# 创建conda虚拟环境
conda create -n 环境名 python=python版本号
# 激活环境名
conda activate 环境名

"""
	例子：
		# 创建conda虚拟环境
        conda create -n open-mmlab python=3.8
        # 激活环境名
        conda activate open-mmlab
"""
 
# 安装pytorch, 官网链接: https://pytorch.org/, 选择合适的pytorch版本
# 一般选择： stable Linux pip python cudaxx, cudaxx与之前查看的cuda版本有关
# 针对C2403 180服务器在2022-3-30时的状态, 安装命令如下
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu113

```

# step 2: 安装MMdetection

说明：

>官网推荐使用MIM安装，但是在使用MIM安装时不能准确控制安装路径，所以这里建议手动安装

```python 
""" 安装mmcv-full """
# 下面{cu_version}表示cuda版本, 例如cuda-11.3就是cu113
# 下面{torch_version}表示pytorch版本, 例如pytorch1.7.0就是torch1.7.0
pip install mmcv-full -f https://download.openmmlab.com/mmcv/dist/{cu_version}/{torch_version}/index.html

"""
	针对C2403 180服务器在2022-3-30时的状态, 安装命令如下:
https://download.openmmlab.com/mmcv/dist/cu113/torch1.11.0/index.html
"""

# 安装mmdetection
git clone https://github.com/open-mmlab/mmdetection.git
cd mmdetection
pip install -r requirements/build.txt
pip install -v -e . 

```



# step 3: 检查是否安装成功

1. 下载权重，并保存到checkpoints路径下

   ```python
   # 查看mmdetection目录下是否有checkpoints目录, 没有就创建
   # 假设现在在mmdetection/目录下
   mkdir checkpoints
   cd checkpoints
   # 目前在checkpoints/下
   wget http://download.openmmlab.com/mmdetection/v2.0/faster_rcnn/faster_rcnn_r50_fpn_1x_coco/faster_rcnn_r50_fpn_1x_coco_20200130-047c8118.pth
   # 查看权重是否下载成功
   ls
   # 存在faster_rcnn_r50_fpn_1x_coco_20200130-047c8118.pth则下载成功
   ```

   

2. 写个小demo测试一下

   ```Python
   # 假设现在在mmdetection/目录下
   cd demo
   # 目前在demo/下
   # 创建demo.py, 并写入下面内容
   ```

   ```python
   # demo.py
   from mmdet.apis import init_detector, inference_detector
   
   config_file = 'configs/faster_rcnn/faster_rcnn_r50_fpn_1x_coco.py'
   # 从 model zoo 下载 checkpoint 并放在 `checkpoints/` 文件下
   # 网址为: http://download.openmmlab.com/mmdetection/v2.0/faster_rcnn/faster_rcnn_r50_fpn_1x_coco/faster_rcnn_r50_fpn_1x_coco_20200130-047c8118.pth
   checkpoint_file = 'checkpoints/faster_rcnn_r50_fpn_1x_coco_20200130-047c8118.pth'
   device = 'cuda:0'
   # 初始化检测器
   model = init_detector(config_file, checkpoint_file, device=device)
   # 推理演示图像
   inference_detector(model, 'demo/demo.jpg')
   ```

   

3. 测试

   ```Python
   # 假设现在在mmdetection/目录下
   python demo/demo.py
   # 没有报错则安装成功
   ```

# reference

官方文档: https://github.com/open-mmlab/mmdetection/blob/master/docs/zh_cn/get_started.md

