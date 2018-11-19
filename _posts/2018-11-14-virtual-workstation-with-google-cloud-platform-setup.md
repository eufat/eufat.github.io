---
title: Virtual Workstation with Google Cloud Platform
---

## Background

Ever wondered to have a high specs workstation without all the noise, space and maintenance cost? well maybe in the past you cannot do that. Now with high-speed internet connection coupled with any laptop, you can have a high-end workstation that does all the graphics-intensive workloads such as rendering, visualization and gaming.

## Prerequisites

Before we go any further let's break down what is your prerequisites.

-   PC or Mac
-   High-speed and low latency internet (10Mbps minimum speed and 30ms maximum latency)
-   Google Cloud Platform account with credits

## Create A New VM Instance

For this tutorial, we will use Google Cloud Compute Engine. I assume you have add credits or trial credits to your account so the VM is billable. This is the step-by-step guide.

1. Open [Google Cloud Console](https://console.cloud.google.com) in your browser.
2. Hit that menu and choose Compute Engine, then create a new instance.
3. Choose the nearest region.
4. This is the important part, in machine type section. You can choose any machine type, but for me, 4 vCPUs (n1-standard-4) is enough. At CPU platform selection, I believe that the Skylake is the best option to date. One thing to note that 4 vCPUs mean that the VM instance will account for four CPU thread, not real four logical core (because of Intel Hyper-Threading). So, every 2 vCPUs is equivalent with to one logical core.
5. For the GPU, just make sure you choose the one with Virtual Workstation. At the time of writing, there is NVIDIA Tesla [P4](http://images.nvidia.com/content/pdf/grid/data-sheet/nvidia-p4-datasheet.pdf) and [P100](https://images.nvidia.com/content/tesla/pdf/nvidia-tesla-p100-PCIe-datasheet.pdf) GPU ([T4 is coming](https://cloud.google.com/blog/products/compute/google-cloud-first-to-offer-nvidia-tesla-t4-gpus) with RTX technology). To compare with NVIDIA consumer GPU, referring to [this](https://www.techpowerup.com/gpu-specs) the [P4 is equivalent with GTX 1060](https://www.techpowerup.com/gpu-specs/tesla-p4.c2879), [P100 with GTX 1080](https://www.techpowerup.com/gpu-specs/tesla-p100-pcie-16-gb.c2888) and [T4 with RTX 2070](https://www.techpowerup.com/gpu-specs/tesla-t4.c3316). I choose the P4 because it is the only cheapest option to date.
6. In Boot disk selection, choose Windows Server 2016 Datacenter with Desktop Experience.
7. To enable traffic from HTTP and HTTPS allow it in the firewall.
8. Check preemptible policy to lower down your bill (it only last 24 hours, but for me, I will never use this workstation 24 hours straight away).

## Estimate the Cost

It's time to calculate the bill each month with [Google Cloud Pricing Calculator](https://cloud.google.com/products/calculator/).

1. In Compute Engine estimation, we got 0.62 USD per hour with the setup above.
2. In storage, we got 4.62 USD per month with 100 GB of Standard Persistent Disk.
3. Google Cloud does not bill our ingress network (network into the server), but [bill the egress](https://cloud.google.com/compute/pricing#internet_egress). So keep that in mind too.

I think this is a pretty good deal since for this kind of workstation we would pay over a thousand bucks and another thousand for the maintenance, electricity, network and overhead cost if we buy a real one.

## Software Setup

This is the basic software setup, we will use RDP to log on to our virtual workstation.

1. Set Windows Password on the console, copy the password on somewhere else. We will change this password later.
2. Install the [Chrome RDP for Google Cloud Platform extension](https://chrome.google.com/webstore/detail/chrome-rdp-for-google-clo/mpbbnannobiobpnfblimoapbephgifkm).
3. Open the RDP and use the password before to log in to the instance.
4. After logged on, turn off IE Enhanced Security Configuration.
5. Setup a second account with the password you can remember. To do so, right click on Windows start menu, click Computer Management, lastly Setup a New User account.
6. Use IE to download and install the [NVIDIA GRID driver](https://storage.googleapis.com/vwkstn-grid/391.81_grid_win10_server2016_64bit_international.exe).
7. Use IE again to download and install [VB-Audio Cable driver](https://www.vb-audio.com/Cable/index.htm) to enable audio.
8. I recommend using the [Windows Remote Desktop](https://support.microsoft.com/en-ca/help/4028379/windows-10-how-to-use-remote-desktop) or [Microsoft Remote Desktop 10](https://itunes.apple.com/us/app/microsoft-remote-desktop-10/id1295203466?mt=12) for Mac.

## Advanced Software Setup

Use this setup if you want to maximize the workstation resolution or want a lower input lag (for gaming). Since at the basic setup it will only produce maximum 1366x768 pixel resolution and quite hefty input lag.

1. To maximize the resolution in NVIDIA Control Panel, you need to enable the NVIDIA Quadro vDWS. Ask for software download and read the documentation carefully to install at [here](https://www.nvidia.com/object/vgpu-evaluation.html).
2. To lower the input lag, you can use [Parsec](https://parsecgaming.com/) as it enables nifty software tricks to reduce input lag as an alternative to RDP. You need to install on both ends (client and host) and enable as a hosting in the virtual workstation.

## Personal Experience

Well, I think it felt like magic when your laptop (for me it is my lightweight X1 Carbon) can do any heavy lifting without breaking a sweat, no lousy noise, no beefy hardware and just the amazing works of software.
