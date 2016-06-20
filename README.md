# Extemporize

## motivation

- flow
- low barrier to investigation
- prototype -> project

## irb

- [Charlie's walkthrough](https://youtu.be/QMsbyBQmmkI?t=9m16s)
  - using [Tom's Gem](https://rubygems.org/gems/jmx)

## groovysh

### `:grab`

- current: https://github.com/Dispader/groovysh-command-grab
- on the way into the Groovy core

### get available heap memory

```Groovy
import java.lang.management.ManagementFactory
used = ManagementFactory.memoryMXBean.heapMemoryUsage.used
```

### JVM management beans + basic UI + threadding

```Groovy
303  import javax.swing.JFrame
 304  import javax.swing.JLabel
 305  frame = new JFrame('heap usage')
 306  label = new JLabel('000000000')
 307  frame.contentPane.add(label)
 308  frame.visible = true
 309  frame.alwaysOnTop = true
 310  frame.pack()
 311  label.font = label.font.deriveFont 40
 312  label.font = label.font.deriveFont(40)
 313  frame.pack()
 314  label.font = label.font.deriveFont(100)
 315  frame.pack()
 316  frame.contentPane.add(label)
 317  frame.pack()
 318  label.font = label.font.deriveFont(40.0)
 319  frame.pack()
 320  label.font = label.font.deriveFont(80.0)
 321  frame.pack()
 322  label.text = java.lang.management.ManagementFactory.memoryMXBean.heapMemoryUsage.used
 323  sleep 1
 324  sleep 10
 325  sleep 100
 326  sleep(1000)
 327  Thread.start { sleep 1000; label.text = java.lang.management.ManagementFactory.memoryMXBean.heapMemoryUsage.used }
 328  label.text = java.lang.management.ManagementFactory.memoryMXBean.heapMemoryUsage.used
 329  String getHeap() { java.lang.management.ManagementFactory.memoryMXBean.heapMemoryUsage.used }
 330  getHeap()
 331  Thread.start { sleep 1000; label.text = getHeap() }
 332  Thread.start { while(true) { sleep 1000; label.text = getHeap() } }
 333  import javax.swing.JFrame
 334  import javax.swing.JLabel
 335  frame = new JFrame('heap usage')
 336  label = new JLabel('000000000')
 337  frame.contentPane.add(label)
 338  frame.visible = true
 339  frame.alwaysOnTop = true
 340  frame.pack()
 341  label.font = label.font.deriveFont(40.0)
 342  frame.pack()
 343  Thread.start { while(true) { sleep 1000; label.text = getHeap() } }
 344  String getHeap() { java.lang.management.ManagementFactory.memoryMXBean.heapMemoryUsage.used }
 345  Thread.start { while(true) { sleep 1000; label.text = getHeap() } }
 346  frame.setVisible false
```

### Grab command

```Groovy
:load https://git.io/v2N1I
:register GrabCommand

:grab 'com.j256.simplejmx:simplejmx:1.12'
```

### explore a new library

- currently exploring [the SharePoint Guava turorial](http://www.tutorialspoint.com/guava/guava_overview.htm)

- only displayed command-line; loop-show example in Charlie's talk is more interesting
