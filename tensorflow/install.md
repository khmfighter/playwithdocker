1、确保安装好docker和docker-compose环境
   可以通过pip install进行安装
2、下载相关示例代码
   git clone https://github.com/aymericdamien/TensorFlow-Examples.git
3、同等目录下创建tensorflow运行的docker-compose.yml文件
   version: '2'
   services:
     jupyter:
       image: registry.cn-hangzhou.aliyuncs.com/denverdino/tensorflow
       container_name: jupyter
       ports:
         - "8888:8888"
       environment:
         - PASSWORD=tensorflow
       volumes:
         - "/tmp/tensorflow_logs"
         - "./notebooks:/root/notebooks"
       command:
         - "/run_jupyter.sh"
         - "--allow-root"   #该配置必须，否则无法启动jupyter
         - "/root/notebooks"
    tensorboard:
       image: registry.cn-hangzhou.aliyuncs.com/denverdino/tensorflow
       container_name: tensorboard
       ports:
         - "6006:6006"
       volumes_from:
         - jupyter
       command:
         - "tensorboard"
         - "--logdir"
         - "/tmp/tensorflow_logs"
         - "--host"
         - "0.0.0.0"
4、通过http://IP:8888访问Tensorflow的Jupyter交互实验环境，登录密码为: tensorflow
5、通过http://IP:6006 从浏览器中访问模型可视化工具TensorBoard
6、运行http://IP:8888/notebooks/4_Utils/tensorboard_basic.ipynb 来实验Tensorboard
