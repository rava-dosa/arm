---
layout: post
title: Dialogues on linux kernel-2
subtitle: Adding a new Syscall
tags: [tutorial, software, linux, kernel, os]
---
### Architecture of Linux kernel
![Linux-Architecture](https://i.pinimg.com/originals/a4/76/e5/a476e5ac785fa192712b24316bfaf3c3.gif){:class="img-responsive"}
### Before We start
This series is neither totally theoritical nor totally hands-on. It is amalgammation of both. Just the way I think. You will not become expert which should be implied.  
### What is Syscall ?
System call is the programmatic way in which a computer program requests a service from the kernel of the operating system it is executed on. This may include hardware-related services (for example, accessing a hard disk drive), creation and execution of new processes, and communication with integral kernel services such as process scheduling. [Ref](https://en.wikipedia.org/wiki/System_call)
### Some Syscall

{% highlight c %}
#ifndef CONFIG_ARCH_HAS_SYSCALL_WRAPPER
asmlinkage long sys_io_setup(unsigned nr_reqs, aio_context_t __user *ctx);
asmlinkage long sys_io_destroy(aio_context_t ctx);
asmlinkage long sys_io_submit(aio_context_t, long,
			struct iocb __user * __user *);
asmlinkage long sys_io_cancel(aio_context_t ctx_id, struct iocb __user *iocb,
			      struct io_event __user *result);
asmlinkage long sys_io_getevents(aio_context_t ctx_id,
				long min_nr,
				long nr,
				struct io_event __user *events,
				struct timespec __user *timeout);
asmlinkage long sys_io_pgetevents(aio_context_t ctx_id,
				long min_nr,
				long nr,
				struct io_event __user *events,
				struct timespec __user *timeout,
				const struct __aio_sigset *sig);

/* fs/xattr.c */
asmlinkage long sys_setxattr(const char __user *path, const char __user *name,
			     const void __user *value, size_t size, int flags);
asmlinkage long sys_lsetxattr(const char __user *path, const char __user *name,
			      const void __user *value, size_t size, int flags);
asmlinkage long sys_fsetxattr(int fd, const char __user *name,
			      const void __user *value, size_t size, int flags);
asmlinkage long sys_getxattr(const char __user *path, const char __user *name,
			     void __user *value, size_t size);
asmlinkage long sys_lgetxattr(const char __user *path, const char __user *name,
			      void __user *value, size_t size);
asmlinkage long sys_fgetxattr(int fd, const char __user *name,
			      void __user *value, size_t size);
asmlinkage long sys_listxattr(const char __user *path, char __user *list,
			      size_t size);
asmlinkage long sys_llistxattr(const char __user *path, char __user *list,
			       size_t size);
asmlinkage long sys_flistxattr(int fd, char __user *list, size_t size);
asmlinkage long sys_removexattr(const char __user *path,
				const char __user *name);
asmlinkage long sys_lremovexattr(const char __user *path,
				 const char __user *name);
asmlinkage long sys_fremovexattr(int fd, const char __user *name);

/* fs/dcache.c */
asmlinkage long sys_getcwd(char __user *buf, unsigned long size);

/* fs/cookies.c */
asmlinkage long sys_lookup_dcookie(u64 cookie64, char __user *buf, size_t len);

/* fs/eventfd.c */
asmlinkage long sys_eventfd2(unsigned int count, int flags);

/* fs/eventpoll.c */
asmlinkage long sys_epoll_create1(int flags);
asmlinkage long sys_epoll_ctl(int epfd, int op, int fd,
				struct epoll_event __user *event);
asmlinkage long sys_epoll_pwait(int epfd, struct epoll_event __user *events,
				int maxevents, int timeout,
				const sigset_t __user *sigmask,
				size_t sigsetsize);

/* fs/fcntl.c */
asmlinkage long sys_dup(unsigned int fildes);
{% endhighlight %}

