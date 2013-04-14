TINY-Web
========

一个学习linux网络编程的小Web服务器
--

记录一些比较重要有意思的知识点：
--
--
--
rio.h和rio.c是一个封装read/write的结构体和操作函数。
--
--
rio.h定义结构体，把文件描述符关联到一个结构体里面，这个结构体封装一个缓冲区。
rio_readn/rio_writen是无缓冲的输入输出函数
而rio_readnb/rio_readlineb是带缓冲的输入，分别是最多读入n个字节和一行(<maxlen)字节到usrbuf。
后两个带缓冲的输入利用了static函数rio_read。这个函数类似于linux的read，不过rio_read自带缓冲区而已。
---

parse_uri函数L163的index函数在linux下strings.h有定义，等同于strchr(const char * str, int character)。L166的*ptr = '\0';很重要，把这句代码和L171的strcat(filename, uri);联系起来看看就知道了。
---			 
serve_dynamic函数L225的dup2函数，需要好好理解理解。



总体通信模型很简单：C-S，server端把connfd传给一个doit函数，具体操作全是在doit函数里进行，操作完以后close(connfd)。
主要学习学习read/write的封装、struct stat的应用、mmapmunmap、fork、setenv/getenv、dup2、execve、wait、sprintf
和几个string处理函数：strstr、strchr、strcasecmp、（ptr = index(SrcStr, character); strcpy(destStr, ptr+1); *ptr = '\0'; ...）

			 
