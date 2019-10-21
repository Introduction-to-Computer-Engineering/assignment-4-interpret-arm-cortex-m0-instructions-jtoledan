### Reference
All the instruction links and one of the footnotes come from this [ARM Cortex-M0 User Guide](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0497a/BABIHJGA.html).

### Interpretation assignment
| Label | Instruction | Intepretation |
| --- | --- | --- |
| negate: | | _Label (corresponds to the address of the first following instruction)_ |
| | [sub](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #8` | Subtact 8 from the stack pointer (and store into the stack pointer) |
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r0, [sp, #4]`<sup>[1](#footnotes)</sup> | Write (the contents of) r0 to the memory with address sp + 4 |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | |
| | [rsbs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)    `r3, r3, #0` | |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` | moves r3 into r0|
| | [add](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #8` | Adds sp and #8|
| | [bx](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)      `lr` | |
| | | |
| main: | | _Label (corresponds to the address of the first following instruction)_ |
| | [push](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIAJHJ.html)    `{lr}` | |
| | [sub](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #12` | |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, #6` | Stores #6 into r3. |
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | |
| | [cmp](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIHIEI.html)     `r3, #0` | |
| | [ble](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)<sup>[2](#footnotes)</sup>     `.L4` | |
| | [ldr](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` |moves r3 into r0 |
| | [bl](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABEFHAE.html)      `negate` | |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, r0` | moves r0 into r3|
| | [str](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABJGHFJ.html)     `r3, [sp, #4]` | |
| | | |
| .L4: | | _Label (corresponds to the address of the first following instruction)_ |
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r3, #0` | moves #0 int r3|
| | [movs](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABHGAJI.html)    `r0, r3` | moves r3 into r0|
| | [add](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABFFEJF.html)     `sp, sp, #12` | adds sp and #12 and puts them into sp| 
| | [pop](http://infocenter.arm.com/help/topic/com.arm.doc.dui0497a/BABIAJHJ.html)     `{pc}` | |

### Footnotes

**1** _[Addressing modes](http://www.davespace.co.uk/arm/introduction-to-arm/addressing.html)_ 

**2** _[Conditional execution](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0497a/BABEHFEF.html)_ 
