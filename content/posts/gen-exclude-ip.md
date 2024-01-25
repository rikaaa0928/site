---
title: "生成排除置顶ip段后的新ip段"
date: 2024-01-25T18:06:41+08:00
draft: false
tags: ["network", "pytrhon"]
author: ["rikaaa0928"]
categories : ["tools"]
---

```
from ipaddress import ip_network

start = '0.0.0.0/0'
exclude = ['1.1.1.1/32', '10.0.0.0/8']

result = [ip_network(start)]
for x in exclude:
    n = ip_network(x)
    new = []
    for y in result:
        if y.overlaps(n):
            new.extend(y.address_exclude(n))
        else:
            new.append(y)
    result = new

print(','.join(str(x) for x in sorted(result)))
```