# 常用快捷键
  - Tab： 自动补全
  - Ctrl + A：把光标移动到开头
  - Ctrl + E：把光标移动到结尾
  - Ctrl + L：清屏

# 常见命令
  - cd <Path>
  - ls
  - pwd(Print Current Name of Directory)
  - tree
  - rm <file> / -r <document> ,-f表示强制删除，无需确认
  - 创建文件以及文件夹
    - mkdir document
    - touch file
  - cp <file> <dest_file> / -r <document><dest_document>
  - 程序卡死
    - ps -ef 查看当前所有正在运行的进程
    - kill -9 <PID> -9表示强制执行
    - xkill + 点击想要关闭的窗口
  - 挂载硬盘
      - fdisk 盘符路径 进入硬盘操作
      - mkfs.ext4 盘符路径 格式化磁盘并写入系统文件
      - mount  盘符路径  需要挂载的路径 将磁盘挂载在某个地方
  - 寻找某文件
      - updatedb + locate libxxx.so 寻找默认库文件夹中的xxx库
      - apt-file  update + apt-file search libxxx.so 寻找所有叫做该名字的apt库

# Conda操作
  - conda create -n <envname> python==x.x package==x.x ... 创建名为envname的python虚拟环境，其中python版本为x.x，同时下载库package
  - conda/source activate <envname>
  - conda deactivate
  - python3 -m pip install package==x.x -i http://pypi.tuna.tsinghua.edu.cn/simple 在激活的虚拟环境中使用pip安装想要的库，并指定源
  - python -m ipykernel install --user --name=xxx 想要在jupyterlab中使用对应的环境，要在该环境激活的情况下输入这行命令
  - conda remove --name env_name --all 删除环境
