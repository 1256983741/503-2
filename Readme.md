1.install cuda

官网下载所需版本的cuda[https://developer.nvidia.com/cuda-toolkit-archive](url)
版本根据实验需求选择

    wget https://developer.download.nvidia.com/compute/cuda/11.3.1/local_installers/cuda_11.3.1_465.19.01_linux.run 

    sudo sh cuda_11.3.1_465.19.01_linux.run

终端出现窗口：
Do you accept the above EULA? (accept / decline / quit):

    accept

回车键进行勾选，X就是选中，没有X就是没有选中，把（driver）安装驱动进行取消。之后向下键，回车确认

最后点击：

    install

2.配置cuda环境

    sudo  vim ~/.bashrc 

在bashrc文件最下方，添加下入代码
（ps：这边需要注意cuda的版本，版本不同，路径的命名需修改）

    export PATH=$PATH:/usr/local/cuda-11.8/bin

    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.8/lib64

    #更新环境
    source ~/.bashrc

3.测试

    nvcc -V

输出下述结果，表示安装成功:
    
    nvcc: NVIDIA (R) Cuda compiler driver
    Copyright (c) 2005-2022 NVIDIA Corporation
    Built on Wed_Sep_21_10:33:58_PDT_2022
    Cuda compilation tools, release 11.3, V11.3.89
    Build cuda_11.3.r11.3/compiler.31833905_0

4.安装cudnn

下载cuda对应版本的cudnn包 https://developer.nvidia.com/rdp/cudnn-archive

将压缩包，放入自定义路径后，输入命令进行解压

    tar -xvf cudnn-linux-x86_64-8.2.0.53_cuda11-archive.tar.xz 

解压后，输入命令，讲cuDNN对应文件拷贝至CUDA指定路径

    cd cudnn-linux-x86_64-8.2.0.53_cuda11-archive/

    ls

    #include  lib  LICENSE

    sudo cp include/cudnn*.h /usr/local/cuda-11.3/include

    sudo cp lib/libcudnn* /usr/local/cuda-11.3/lib64

    sudo chmod a+r /usr/local/cuda-11.3/include/cudnn*.h /usr/local/cuda-11.3/lib64/libcudnn*

5.cuda版本切换

    #修改bashrc
    sudo vim ~/.bashrc

将原先的cuda-11.3注释掉，添加cuda-11.x新的环境设置，即可

    cuda-11.3
    export PATH=$PATH:/usr/local/cuda-11.3/bin
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.3/lib64

    cuda-11.x
    export PATH=$PATH:/usr/local/cuda-11.1/bin
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.x/lib64
