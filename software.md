1. Ghostscript
    PostScipt 语言和pdf解释器,压缩pdf用

    安装
    sudo apt-get install ghostscript

    gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dBATCH -dQUIET -sOutputFile=output.pdf input.pdf
    不同的压缩模式 
    -dPDFSETTINGS=/screen,压缩比最大，输出文件最小，质量最低
    -dPDFSETTINGS=/ebook,压缩比稍小，输出文件稍大，质量稍高
    -dPDFSETTINGS=/prepress,输出文件信息同Acrobat Distiller “Prepress Optimized”设置
    -dPDFSETTINGS=/default,缺省的，即大多数情况使用的压缩方式

2. pdftk 1.pdf 2.pdf 3.pdf cat output 123.pdf
    合并pdf用

3. conda create -n tf-gpu tensorflow-gpu python=3.6.8

4. sudo apt install default-jre

5. sudo apt install default-jdk

6. Google Cloud: image vs snapshot:
    Snapshots:
    Good for backup and disaster recovery
    Lower cost than images
    Smaller size than images since it doesn't contain OS, etc.
    Differential backups - only the data changed since the last snapshot is recreated
    Faster to create than images
    Snapshots are only available in the project they are created
    Can be created for running disks even while they are attached to running instances
    
    Images:
    Good for reusing compute engine instance states with new instances
    Available across different projects
    Can't be created for running instances(unless you use --force flag)

7. github 常用命令
    git pull origin res12

    git branch --set-upstream-to=origin/res12 double_loss

    git commit --amend

    git stash

    git stash apply

    git remote add upstream https://github.com/open-mmlab/mmdetection.git
    git remote -v
    git fetch upstream
    git merge upstream/master
    git log
    git push origin master
    
    git update-index --assume-unchanged xxx
    git rm --cached xxx


8. pytorch 多卡训练
    如果单进程，num_workers = 0 的话，可以考虑在dataloader里就加上.cuda()，这样显存完全均衡的。
    如果num_worker不为0，使用多进程训练会快，但是dataloader就需要完全放到cpu上，进网络之前.cuda()让pytorch分配。
