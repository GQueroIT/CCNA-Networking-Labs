# Lessons Learned - STP Basics

- STP does not remove physical loops, it logically blocks them
- The Root Bridge never has blocking ports
- Non-root switches always have exactly one Root Port
- Blocking ports serve as backup paths for redundancy
- Changing bridge priority directly impacts root election
- Changing interface cost influences path selection
- STP reconvergence introduces temporary network disruption
- Understanding STP behavior is essential for real-world troubleshooting