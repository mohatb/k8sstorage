# Benchmark Azure File with dynamic premium storage class

disk size is 100GB

```bash
root@dynamicazurefilepremiumdeploy-7c9dcf94ff-l6xzc:/mnt/azurefiledynamicpremium# fio --randrepeat=1 --ioengine=libaio --direct=1 --gtod_reduce=1 --name=fiotest --filename=testfio --bs=4k --iodepth=64 --size=1G --readwrite=randrw --rwmixread=75
fiotest: (g=0): rw=randrw, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=64
fio-3.25
Starting 1 process
fiotest: Laying out IO file (1 file / 1024MiB)
Jobs: 1 (f=1): [m(1)][100.0%][r=26.6MiB/s,w=9145KiB/s][r=6798,w=2286 IOPS][eta 00m:00s]
fiotest: (groupid=0, jobs=1): err= 0: pid=719: Fri Feb 11 15:38:36 2022
  read: IOPS=7524, BW=29.4MiB/s (30.8MB/s)(768MiB/26116msec)
   bw (  KiB/s): min=21248, max=38688, per=99.93%, avg=30074.75, stdev=4558.99, samples=52
   iops        : min= 5312, max= 9672, avg=7518.67, stdev=1139.74, samples=52
  write: IOPS=2513, BW=9.82MiB/s (10.3MB/s)(256MiB/26116msec); 0 zone resets
   bw (  KiB/s): min= 7040, max=13024, per=99.92%, avg=10046.21, stdev=1569.69, samples=52
   iops        : min= 1760, max= 3256, avg=2511.54, stdev=392.42, samples=52
  cpu          : usr=2.42%, sys=18.88%, ctx=129545, majf=0, minf=5
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=0.1%, >=64=100.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.1%, >=64=0.0%
     issued rwts: total=196498,65646,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=64

Run status group 0 (all jobs):
   READ: bw=29.4MiB/s (30.8MB/s), 29.4MiB/s-29.4MiB/s (30.8MB/s-30.8MB/s), io=768MiB (805MB), run=26116-26116msec
  WRITE: bw=9.82MiB/s (10.3MB/s), 9.82MiB/s-9.82MiB/s (10.3MB/s-10.3MB/s), io=256MiB (269MB), run=26116-26116msec
root@dynamicazurefilepremiumdeploy-7c9dcf94ff-l6xzc:/mnt/azurefiledynamicpremium#
```
