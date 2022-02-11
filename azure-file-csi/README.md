# Benchmark Azure File with dynamic storage class and CSI driver

disk size is 100GB

```bash
root@nginx-azurefile-csi:/mnt/azurefiledynamic# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=fiotest --filename=testfio --bs=4k --iodepth=64 --size=1G --readwrite=randrw --rwmixread=75
fiotest: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.25
Starting 1 process
fiotest: Laying out IO file (1 file / 1024MiB)
Jobs: 1 (f=1): [m(1)][100.0%][r=2842KiB/s,w=944KiB/s][r=710,w=236 IOPS][eta 00m:00s]
fiotest: (groupid=0, jobs=1): err= 0: pid=715: Fri Feb 11 14:04:02 2022
  read: IOPS=652, BW=2610KiB/s (2672kB/s)(768MiB/301186msec)
   bw (  KiB/s): min=  720, max= 4000, per=100.00%, avg=2611.01, stdev=796.71, samples=602
   iops        : min=  180, max= 1000, avg=652.72, stdev=199.16, samples=602
  write: IOPS=217, BW=872KiB/s (893kB/s)(256MiB/301186msec); 0 zone resets
   bw (  KiB/s): min=  192, max= 1336, per=100.00%, avg=872.28, stdev=274.21, samples=602
   iops        : min=   48, max=  334, avg=218.04, stdev=68.53, samples=602
  cpu          : usr=0.42%, sys=2.38%, ctx=206411, majf=0, minf=8
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=196498,65646,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=2610KiB/s (2672kB/s), 2610KiB/s-2610KiB/s (2672kB/s-2672kB/s), io=768MiB (805MB), run=301186-301186msec
  WRITE: bw=872KiB/s (893kB/s), 872KiB/s-872KiB/s (893kB/s-893kB/s), io=256MiB (269MB), run=301186-301186msec
root@nginx-azurefile-csi:/mnt/azurefiledynamic#
```
