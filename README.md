# Notes on Google’s GFS (SOSP 2003)

## Link to an article / paper
- **The Google File System (SOSP 2003)** - Sanjay Ghemawat, Howard Gobioff, Shun-Tak Leung  
- [The Google File System (SOSP 2003) - PDF](https://research.google.com/archive/gfs-sosp2003.pdf)

## What I find interesting about it
What makes this paper feel like *real software engineering* (not just theory) is how explicitly it designs around reality: machines fail all the time, data is huge, and the goal is high aggregate throughput on commodity hardware. GFS is intentionally not a "perfect POSIX file system." Instead, it chooses trade-offs that match Google's workload (large files, streaming reads, and lots of appends) and then builds a system that stays useful under constant failure. 

I also like how clean the architecture is: a single master manages metadata, but data doesn't flow through the master-clients talk to chunkservers directly. That's a very "engineer brain" move: separate control plane from data plane to avoid a throughput bottleneck, even if it introduces other constraints you must manage (replication, leases, recovery). 

## Quick takeaways (for myself)
- Design starts from **workload assumptions**, not from "ideal correctness."
- **Fault tolerance** is a feature, not an afterthought.
- Clear **API/consistency contracts** matter more than pretending the world is perfect.

