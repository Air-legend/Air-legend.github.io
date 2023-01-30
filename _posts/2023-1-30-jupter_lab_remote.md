---
title: 局域网远程连接jupyter notebook lab
author: bean
date: 2023-1-30 12:10:00 +0800
categories: [tools]
tags: [jupyter notebook]
---
# 安装

## 1. 安装 conda/miniconda并进行初始化

## 2. 安装 jupyterlab
    > conda install -c conda-forge jupyterlab

# 配置
## 1. 创建 config 文档
    > jupyter notebook --generate-config
## 2. 设置登录密码
    > jupyter notebook password
## 3. 配置config

    文件一般保存在 ~/.jupyter/jupyter_notebook_config.py

    > c.NotebookApp.notebook_dir = '/home/digisky/notebooks' \
    > c.NotebookApp.ip='*' # 允许所有ip访问 \
    > c.NotebookApp.open_browser = False # 不打开浏览器 \
    > c.NotebookApp.port =8872 #指定端口，不要用默认8888端口！公网上不用默认端口是好文明 \
    > c.NotebookApp.allow_remote_access = True #允许远程机器访问

## 3. 加入想要使用的conda环境
    > python -m ipykernel install --user --name xx --display-name "显示的名字"

添加过后可通过 jupyter kernelspec list 查看

## 4. 如果显示加载conda环境错误，修改conda kernel的路径
    文件一般保存在 ~/.local/share/jupyter/kernels
    将其中的 **kernel.json** 文件中的解释器路径修改为 /home/digisky/miniconda3/envs/xx/bin/python 路径

# 启动
    > jupyter lab -p 8872
