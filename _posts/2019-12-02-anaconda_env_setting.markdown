---
layout: post
title: anaconda env path settings for multiple CUDA versions
date: 2019-12-02 01:37
description: 
---
**Set `activate.d` and `deactive.d` so that everytime you activate your anaconda env, it addes the paths to your env for you.** 

---- 
`activate.d`

* `$ mkdir -p /span/home/USER_NAME/.conda/envs/ENV_NAME/etc/conda/activate.d/`

* `$ vi /span/home/USER_NAME/.conda/envs/ENV_NAME/etc/conda/activate.d/activate.sh`

* Add the following into `activate.sh` (you have to change cuda-X.Y into your preferred CUDA version e.g., cuda-10.0)

{% highlight shell %}
#!/bin/sh
ORIGINAL_PATH=$PATH
export PATH=/usr/local/cuda-X.Y/bin:${PATH}

ORIGINAL_LD_LIBRARY_PATH=$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=/usr/local/cuda-X.Y/lib64:/usr/local/cuda-X.Y/extras/CUPTI/lib64:/lib/nccl/cuda-X.Y:$LD_LIBRARY_PATH
{% endhighlight %}

* `chmod +x /span/home/USER_NAME/.conda/envs/ENV_NAME/etc/conda/activate.d/activate.sh`

----
 `deactivate.d`
 
* `$ mkdir -p /span/home/USER_NAME/.conda/envs/ENV_NAME/etc/conda/deactivate.d`

* `$ vi /span/home/USER_NAME/.conda/envs/ENV_NAME/etc/conda/deactivate.d/deactivate.sh`

* Add the following into `deactivate.sh` 

{% highlight shell %}
#!/bin/sh

export PATH=$ORIGINAL_PATH
unset ORIGINAL_PATH
export LD_LIBRARY_PATH=$ORIGINAL_LD_LIBRARY_PATH
unset ORIGINAL_LD_LIBRARY_PATH
{% endhighlight %}

* `chmod +x /span/home/USER_NAME/.conda/envs/ENV_NAME/etc/conda/deactivate.d/deactivate.sh`

----

**Or you can simply run a bash file something like `cuda-10.0.sh` every time you need a specfic CUDA version (e.g., cuda-10.0)**

`cuda-10.0.sh`

{% highlight shell %}
#!/bin/sh
export PATH=/usr/local/cuda-10.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda−10.0/lib64:/usr/local/cuda−10.0/extras/CUPTI/lib64:${LD_LIBRARY_PATH}
{% endhighlight %}


--- 
**Reference**

<http://blog.kovalevskyi.com/multiple-version-of-cuda-libraries-on-the-same-machine-b9502d50ae77>
