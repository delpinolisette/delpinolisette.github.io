---
title: "Integration Thoughts"
author: Lisette del Pino
layout: post
---

{{ page.last_modified_at }}

# Integration Thoughts

There are some tricky assumptions about integration that need to be addressed:

We know this from optimization theory - we need to be careful about integrating a function using usual methods - it could be the case in higher dimensions that a function is **not** integrable. 

To prove that it is indeed Riemann integrable, we need to show that the measure of the boundary of the region has volume zero . This is also equivalent to showing:

- the region is a Jordan region [(what's that?)](https://math.stackexchange.com/questions/1251627/jordan-region-problem), or that
- the set to integrate over is admissible, or that
- the boundary of the volume to integrate is zero


Also... happy pi day!!! 