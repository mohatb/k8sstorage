# Benchmark Azure File with dynamic storage class and CSI driver premium

disk size is 100GB

```bash
root@nginx-azurefile-csi-premium-77cd95b7bd-b9gnp:/mnt/azurefiledynamiccsipremium# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=fiotest --filename=testfio --bs=4k --iodepth=64 --size=1G --readwrite=randrw --rwmixread=75
fiotest: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.25
Starting 1 process
fiotest: Laying out IO file (1 file / 1024MiB)
Jobs: 1 (f=1): [m(1)][100.0%][r=28.7MiB/s,w=9877KiB/s][r=7339,w=2469 IOPS][eta 00m:00s]
fiotest: (groupid=0, jobs=1): err= 0: pid=731: Fri Feb 11 15:14:23 2022
  read: IOPS=5942, BW=23.2MiB/s (24.3MB/s)(768MiB/33064msec)
   bw (  KiB/s): min=10144, max=34992, per=100.00%, avg=29055.33, stdev=3857.91, samples=54
   iops        : min= 2536, max= 8748, avg=7263.78, stdev=964.50, samples=54
  write: IOPS=1985, BW=7942KiB/s (8132kB/s)(256MiB/33064msec); 0 zone resets
   bw (  KiB/s): min= 3408, max=11896, per=100.00%, avg=9704.83, stdev=1345.53, samples=54
   iops        : min=  852, max= 2974, avg=2426.17, stdev=336.38, samples=54
  cpu          : usr=2.41%, sys=15.57%, ctx=121905, majf=0, minf=6
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=196498,65646,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=23.2MiB/s (24.3MB/s), 23.2MiB/s-23.2MiB/s (24.3MB/s-24.3MB/s), io=768MiB (805MB), run=33064-33064msec
  WRITE: bw=7942KiB/s (8132kB/s), 7942KiB/s-7942KiB/s (8132kB/s-8132kB/s), io=256MiB (269MB), run=33064-33064msec
root@nginx-azurefile-csi-premium-77cd95b7bd-b9gnp:/mnt/azurefiledynamiccsipremium#
```
