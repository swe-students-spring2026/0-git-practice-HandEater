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

---

# Comments from Mumu Li

- This paper is probably one of the most influential systems papers of the last two decades that even as a CS sophomore I had long ago heard of it. It's still relavant today, for example, Section 2.4 is a masterclass in pragmatic engineering, since it strict correctness for performance in a way that the application developers can tolerate; And Section 2.3 is a great example of questioning "standard" constants (like 4KB blocks) based on specific workload data.
- You cannot discuss GFS without mentioning Hadoop. The GFS paper (along with the MapReduce paper) was reverse-engineered by Doug Cutting and Mike Cafarella to create HDFS (Hadoop Distributed File System). The open-source big data revolution was essentially built on a replica of the design described in this paper. If GFS hadn't been published, the "Big Data" ecosystem (Cloudera, Hortonworks, Spark, etc.) might have looked very different or arrived much later.
- Especially loved how it didn't try to solve every problem, but solved the specific problems Google had at the time (crawling the web) using the cheapest hardware available, and in doing so, it changed the entire software industry.