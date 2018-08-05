---
layout: post
title: A monologue on linux kernel
subtitle: Linux starter pack
tags: [tutorial, software, linux, kernel, os]
---
### Architecture of Linux kernel
![Linux-Architecture](https://i.pinimg.com/originals/a4/76/e5/a476e5ac785fa192712b24316bfaf3c3.gif){:class="img-responsive"}
### Before We start
This is neither totally theoritical nor totally hands-on. It is amalgammation of both. Just the way I think. You will not become expert which is subtle.  
### Adding a new module in linux kernel
So linux kernel is a monolithic kernel. To be accurate it is Modular monolithic. Monolithic term in kernal is used in the sense of permission of code running there. If the whole kernel is running in ** ring 0 ** then the kernel will be called monoltihic. But if very few code is running in ring 0 then the kernel is called micro kernel architecture.  
So if a module crashes the whole kernel will crash in linux. So always spawn a VM if you are trying to add garbage in linux.
#### Hello World
{% highlight javascript linenos %}  
// hello-1.c - The simplest kernel module.  
#include <linux/module.h>    /* Needed by all modules */
#include <linux/kernel.h>    /* Needed for KERN_INFO */

int init_module(void)
{
    printk(KERN_INFO "Hello world 1.\n");

    /* 
     * A non 0 return means init_module failed; module can't be loaded. 
     */
    return 0;
}

void cleanup_module(void)
{
    printk(KERN_INFO "Goodbye world 1.\n");
}  
{% endhighlight %}



