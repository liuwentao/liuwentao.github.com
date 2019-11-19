

执行yum update以后遇到了如下的问题

> "Cannot retrieve repository metadata (repomd.xml) for repository: fedora. Please verify its path and try again"

修改下面的文件:

> /etc/yum.repos.d/fedora.repo 和 /etc/yum.repos.d/fedora-updates.repo

修改方式为取消注释掉的 baseurl即把前面＃删掉   
然后加上注释到 mirrorlist 即加上＃，保存.

然后就解决了.