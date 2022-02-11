# Benchmark Azure File with dynamic storage class

disk size is 20GB

```bash
root@dynamicazurefilepod:/mnt/azurefiledynamic# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=fiotest --filename=testfio --bs=4k --iodepth=64 --size=1G --readwrite=randrw --rwmixread=75
fiotest: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.25
Starting 1 process
Jobs: 1 (f=1): [m(1)][100.0%][r=2970KiB/s,w=984KiB/s][r=742,w=246 IOPS][eta 00m:00s]
fiotest: (groupid=0, jobs=1): err= 0: pid=723: Fri Feb 11 13:12:29 2022
  read: IOPS=760, BW=3043KiB/s (3116kB/s)(768MiB/258306msec)
   bw (  KiB/s): min= 1424, max= 3832, per=100.00%, avg=3063.66, stdev=272.37, samples=513
   iops        : min=  356, max=  958, avg=765.91, stdev=68.09, samples=513
  write: IOPS=254, BW=1017KiB/s (1041kB/s)(256MiB/258306msec); 0 zone resets
   bw (  KiB/s): min=  400, max= 1336, per=100.00%, avg=1023.38, stdev=117.53, samples=513
   iops        : min=  100, max=  334, avg=255.84, stdev=29.38, samples=513
  cpu          : usr=0.50%, sys=2.58%, ctx=195777, majf=0, minf=7
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=196498,65646,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=3043KiB/s (3116kB/s), 3043KiB/s-3043KiB/s (3116kB/s-3116kB/s), io=768MiB (805MB), run=258306-258306msec
  WRITE: bw=1017KiB/s (1041kB/s), 1017KiB/s-1017KiB/s (1041kB/s-1041kB/s), io=256MiB (269MB), run=258306-258306msec
root@dynamicazurefilepod:/mnt/azurefiledynamic#
```
