# MMdetection Tutorial For C2403

说明：

>time: 2022-03-30
>
>version: v2.23.0
>
>
>
>用途说明：快速入门mmdetection框架，针对官网教程结合实验室已有环境编写。
>
>注：由于typora导出pdf后相对路径会出问题，所以此文本导出为网页版



* <a href="./安装MMdetection.pdf" style="text-decoration:none">Tutorial 1: 安装MMdetection</a>
* <a href="训练自定义数据集.pdf" style="text-decoration:none">Tutorial 2: 训练自定义数据集</a>
* <a href="了解配置文件.pdf" style="text-decoration:none">Tutorial 3: 了解配置文件</a>
* <a href="自定义数据集处理.pdf" style="text-decoration:none">Tutorial 4: 自定义数据集处理</a>
* <a href="数据预处理流程.pdf" style="text-decoration:none">Tutorial 5: 数据预处理流程</a>

对于后面的教程我们使用官网的教程：1. 我现在也没真正的实现过新的模块 2. 官方教程也比较通俗全面 3. 这几节内容复制性差，扩展性强，了解了前面几章再结合官网这几章，应该对mmdetection这个框架有了较为深入的认识。

* <a href="https://mmdetection.readthedocs.io/zh_CN/latest/tutorials/customize_models.html" style="text-decoration:none">Tutorial 6: 自定义模型</a>

  > 主要步骤：
  >
  > 	1. 自定义模块
  > 	1. 注册表注册，为了在使用时能够找到
  > 	1. 配置使用模块

  

* <a href="https://mmdetection.readthedocs.io/zh_CN/latest/tutorials/customize_losses.html" style="text-decoration:none">Tutorial 7: 自定义损失函数</a>

  > 这个教程不太像自定义损失函数，更像是说明怎么更好使用已定义的损失函数，比较重要的是里面总结了一个损失函数的功能，分为以下五点：
  >
  > 1. 设置采样方法为对正负样本进行采样。
  > 2. 通过损失核函数获取**元素**或者**样本**损失。
  > 3. 通过权重张量来给损失**逐元素**权重。
  > 4. 把损失张量归纳为一个**标量**。
  > 5. 用一个**张量**给当前损失一个权重。

* <a href="https://mmdetection.readthedocs.io/zh_CN/latest/tutorials/finetune.html" style="text-decoration:none">Tutorial 8: 微调模型</a>

  > 如果对Tutorial 3了解的话，这一部分是很轻松的，结合相关论文食用效果更佳，但也不是每个模块都要去看论文，适当取舍。

* <a href="https://mmdetection.readthedocs.io/zh_CN/latest/tutorials/init_cfg.html" style="text-decoration:none">Tutorial 9: 权重初始化</a>



关于部署问题，暂时还未到达这一步，以现在的情况看不是最要紧的一块，带后面有需要在看并整理，如有需要，可前往以下链接(网页内提供一键切换中英文)

* <a href="https://mmdeploy.readthedocs.io/zh_CN/latest/" style="text-decoration:none">Tutorial 10: MMdeploy</a>

