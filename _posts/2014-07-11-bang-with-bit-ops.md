---
layout: post
title: "implement ! operator in C with bit ops only"
description: ""
category: "programming"
tags: [c]
---
{% include JB/setup %}

	/* 
	 * bang - Compute !x without using !
	 *   Examples: bang(3) = 0, bang(0) = 1
	 *   Legal ops: ~ & ^ | + << >>
	 *   Max ops: 12
	 *   Rating: 4 
	 */    
    int bang(int x) {
        return ((x | (~x+1))>>31) + 1;
    }

In 2's complement representation, 0 is the only number that its opposite has the same most significant bit as itself, because 0 == -0, 0 == ~0 + 1.
Other numbers have to flip the msb.

For example, 2 is 0x0010 whereas -2 is 0x1110.   
If x is zero, ((x | (~x+1))>>31) will be 0, and the result is 1.    
If x is non-zero, ((x | (~x+1))>>31) will be all 1s, which will be interpreted as -1, and the result is 0.

By exploiting this feature someone produced the elegant code above with only 5 ops. Amazing!