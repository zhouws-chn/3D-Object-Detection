# 3D-Object-Detection

This work is inspired by image-to-3d-bbox(https://github.com/experiencor/image-to-3d-bbox), which is an an implementation of the paper "3D Bounding Box Estimation Using Deep Learning and Geometry" (https://arxiv.org/abs/1612.00496).

Instead of using kitti's 3-D truth, i mainly make two supplements:    
1、Compute 3-D box center by 2-D box and network's output  
2、Compute theta_ray by 2-D box center  
Besides, I make some changes to the code structure.

By now, there are still several problems to be solved, for example:  
1、The number of situations is 256 in this work, whereas it is 64 in the paper.  
2、When detecting, i use objects's truncated and occluded level in kitti's label file to decide whether to generate 3D box, whereas it is reasonable to generate these by the trained neural network.

This is just a raw version, welcome to share your ideas to improve it!

Result on kitti:  
![](C:\Users\zws\Desktop\3D-Object-Detection\output\000000.jpg)

![](C:\Users\zws\Desktop\3D-Object-Detection\output\000003.jpg)

![](C:\Users\zws\Desktop\3D-Object-Detection\output\000006.jpg)

![](C:\Users\zws\Desktop\3D-Object-Detection\output\000007.jpg)

## Useage:

If you want to train, after fixing paths in the train.py, just run:

<pre><code>python3 train.py
</code></pre>

In this way, you can get your own weights file, or you can download the pretrained file from  http://ddl.escience.cn/f/RRk0 ，you need move the file to the **model** direction.
In the detection time, after fixing paths in the detection.py, just run:

<pre><code>python3 detection.py
</code></pre>

## 注意:

上述测试中，我们使用的是kitti数据集，在detection测试的时候，不只是需要image，还需要label。这里的label程序中只取了二位检测框，相当于没有做2D目标检测，而是用2D目标检测的结果来执行3D检测。

cali.txt是相机的校准文件，里面包含了相机的外参和内参。

dataset\test 文件夹中的图片和label均为kitti数据集中的数据。

注:没有测试train，detection是测试过的。
