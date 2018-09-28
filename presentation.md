title: A new way to profile Node.js
layout: true
class: no-counter
<!-- This slide will serve as the base layout for all your slides -->
.bottom-bar-left[
  <a href="http://nearform.com">
    <img src="nearform.svg" alt="nearForm" height="64">
  </a>
]
.bottom-bar-right[
  <div style='letter-spacing:.03em;padding:1.1em'>
    <div style='font-size:0.6em;line-height:1.2em'>
      <a href=https://twitter.com/matteocollina>
        <span class=em>@</span>matteocollina
      </a>
    </div>
  </div>
]

---
class: splash
<p style='margin-top:-1em'></p>
# &nbsp;&thinsp;A .em[new] way <br>to profile<br> Node.em[.]js

<span>Matteo Collina</span>
<a style="border-top:2px solid #fb7a9c;display:block;width:10em;margin-left:auto;margin-right:auto;padding-top:.4em;margin-top:1.3em;margin-bottom:-2.5em" href="http://nearform.com"><img src="nearform.svg" alt="nearForm" height="52"></a>
---

class: impact

# .blink-2[🚨]
## .blink-1[Maximum number of servers] 
## .blink-1[sales traffic dropping]
## .blink-1[angry people are angry]

---

class: impact

# .em[Why] is it slow?

---

class: impact

# because .em[bottleneck]

---

class: impact

# Why is it slow?

<p style='padding: .1em'></p>
.col-5[
## The bottleneck is .em[internal]
<br>
The Node.js process
<br>
is on fire
]

.col-2[
## .center[|]
## .center[|]
## .center[|]
## .center[|]
## .center[|]
]

.col-5[
## The bottleneck is .em[external]
<br>
Something else
<br>
is on fire
]

---

class: impact

# .em[Where] is the bottleneck?

---

# Finding Bottlenecks

.center[.responsive-v[![](opt-process.png)]]


---

# Simulating Load

<div class=logo style='background:rgb(127,127,127);margin-bottom:-1em;height:3.9em;margin-top:0.95em;border: 2px solid #fb7a9c;box-sizing:border-box'>
  .autocannon[![](autocannon.png)]
</div>


.responsive[![](autocannon-demo.gif)]

---

# Finding Bottlenecks

.center[.responsive-v[![](opt-process.png)]]

---

# Diagnostics

[.center[![](clinic.png)]](http://github.com/nearform/node-clinic)


```sh
$ npm install -g clinic
```

---

<a href=http://github.com/nearform/node-clinic style="position:absolute;left:0;top:.5em;width:100%;">
.center[.clinic[![](clinic.png)]] 
</a>
<p style="margin-top: 5.5em"></p>


.col-4[
<a href=http://github.com/nearform/node-clinic-doctor>
.logo[![](doctor.png)]
## Clinic Doctor 
</a>
]

.col-4[
<span>
.logo[![](bp.png)] 
## Clinic Bubbleprof 
</span>
]

.col-4[
<a href=http://github.com/davidmarkclements/0x>
.logo[![](flame.png)]
## Clinic Flame 
</a>
]


---

class: impact

# Clinic Doctor
<a href=http://github.com/nearform/node-clinic-doctor>
.logo[![](doctor.png)]
</a>

Collects metrics by .em1[injecting probes]

Assesses health with .em2[heuristics]

Creates .em3[recommendations]

---

class: impact

# .em[Doctor] metrics

.outline-img[.center[.responsive-v[![](doctor-example.png)]]]


---

class: impact

# Clinic Flame
.logo[![](flame.png)]


Collects metrics by .em1[CPU sampling]

Tracks .em2[top-of-stack] frequency

Creates .em3[flame graphs]


---

# .em[Flame] graphs

.outline-img[.center[.responsive-v[![](flamegraph.png)]]]


---

class: impact

# Clinic Bubbleprof

.logo[![](bp.png)]

Collects metrics using .em1[async_hooks]

Tracks .em2[latency] between operations

Creates .em3[bubble graphs]

---

# Bubble graphs

.outline-img[.center[.responsive-v[![](bubble.png)]]]


---

class: impact

<a href=http://github.com/nearform/node-clinic-doctor>
.logo[![](doctor.png)]
</a>
# .em[Where] is the bottleneck?

---

<p style="margin-top:-2em"></p>
<p style="padding:.1em"></p>
.col-5[
## Clinic Flame
.logo[![](flame.png)]

.center[
For .em[internal] bottlenecks
]

]

.col-2[
## .center[|]
## .center[|]
## .center[|]
## .center[|]
## .center[|]
]

.col-5[
## Clinic Bubbleprof
.logo[![](bp.png)]

.center[
For .em[external] bottlenecks
]
]


---

class: impact

# .em[Live] Hack

.col-4[
<a href=http://github.com/nearform/node-clinic-doctor>
.logo[![](doctor.png)]
</a>
]

.col-4[
<span>
.logo[![](bp.png)] 
</span>
]

.col-4[
<a href=http://github.com/davidmarkclements/0x>
.logo[![](flame.png)]
</a>
]
.col-12[
  <p style="margin-top:1em"></p>
  ## .em[Interact:] <u><http://nf.ie/interact></u>
]

---

.center[
  ![](shaggy.gif)
]


---

class: impact

<h1 style='margin-top:-0.25em'>The .em[Team]</h1>

.team[![](clinic-team.jpg)]

---

class: impact

# Parting Words

---

# Set quantifiable performance goals

> The application should have a response time of 200ms or less in the 99th percentile at 100 concurrent requests per server.

---

class: impact

<p style='margin-top:-2.25em'></p>

# .small[Choose fast libraries]

<p style='padding:.1em'></p>

.col-5[
## Pino
<a href='http://getpino.io'>
.logo[![](pino.png)]
</a>
<br>
High speed .em[logging] library
]

.col-2[
## .center[|]
## .center[|]
## .center[|]
## .center[|]
## .center[|]
]

.col-5[
## Fastify
<a href='http://fastify.io'>
.fastify[.logo[![](fastify.png)]]
</a>
<br>
High speed .em[web] framework
]

---

# Beware of the rabbit hole

* It is not uncommon for .em[80%] of effort to be in the final .em[20%] of optimization work
* Find out what .em[fast enough] is for your given business context
* Remember to .em[balance the cost] of your time against savings and other business gains

---

# You don't .em[always] have to reach..

.center[.responsive-v[![](ludicrous.gif)]]


---
class: splash

# .em[Talk] to us!
## [.em[@]matteocollina](https://twitter.com/matteocollina)
<span>Matteo Collina</span>

<p style="margin-top:2em"></p>

.center[
  <h3 style='color:white;margin-bottom:0.1em'>Let us .em[know] your .em[thoughts]</h3>
  #### <u><https://nf.ie/BPFB></u>
]


<a style="display:block;width:10em;margin-left:auto;margin-right:auto;padding-top:.8em;margin-top:1.7em;margin-bottom:-2.5em" href="http://nearform.com"><img src="nearform.svg" alt="nearForm" height="104"></a>
