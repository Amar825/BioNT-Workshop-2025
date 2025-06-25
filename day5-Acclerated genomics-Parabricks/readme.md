## **Day 4 Reflection – [5 June 2025]**
[Link to the GPU Theory and Hands-on session](https://training.pages.sigma2.no/tutorials/gpu-intro/index.html)

[Link to accelerated genomics theory] (https://coderefinery.github.io/BioNT_Lesson_Accelerated_Genomics/)


### Theory session- Accelerated Genomics (NGS data analysis, GPU introduction) (Sabry Razick, UiO)
#### NVIDIA Parabricks
Parabricks is NVIDIA’s way of making next-generation sequencing (NGS) workflows faster using GPUs. Instead of reinventing the algorithms, they’ve taken standard tools like those from GATK and rewritten them to run on GPUs. This gives you the same outputs, just much faster.

The workflow looks familiar: first, you do read mapping and alignment refinement. Then you move on to variant calling. What changes is the speed. The parts that usually take hours on CPUs now finish in minutes. This can make a huge difference if you're processing a lot of samples or running things in the cloud where time is money.

#### Container image
A container image is like a self-contained box that holds everything you need to run a piece of software. That includes the application itself, its libraries, and all system dependencies. The only thing it uses from your machine is the Linux kernel. This is super helpful in bioinformatics, where some tools are notoriously tricky to set up. With containers, you don’t have to install anything manually or worry about weird compatibility issues. You just pull the image and run it. It saves time and frustration, and makes your analysis reproducible whether you're running it on your laptop, a university cluster, or the cloud.

### Hands-on session
```
docker run \
-it \    # keep it interactive (get a terminal)
--rm \    # remove container after exit (no leftovers)
--gpus all \  # give container access to all GPUs
-v /data:/data \  # mount /data directory (so container can see it)
-v $PWD:$PWD \    # mount current working directory
-w $PWD \ # set working directory inside container to where you are now
nvcr.io/nvidia/clara/clara-parabricks:4.3.0-1 bash # run the NVIDIA Parabricks container and drop into bash```

