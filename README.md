Download Link: https://assignmentchef.com/product/solved-cs410001-project-3
<br>
<strong></strong>






<ol>

 <li>Project Objective

  <ol>

   <li>Based on the single-cycled CPU simulator from project #1, implement a MIPS CPU simulator with memory hierarchy, Translation-Lookaside Buffer (TLB), and virtual page table mechanism. The <strong>memory size</strong>,<strong> page size, cache total size</strong>, <strong>block size</strong> and <strong>set associativity of the cache </strong>should be</li>

   <li>Design and submit your own test case to verify the functionality of the memory hierarchy configuration.</li>

  </ol></li>

</ol>




<ol start="2">

 <li>Project Description</li>

</ol>

The simulator is similar to that of project 1 except the following:

<ol>

 <li>Name the executable <strong>CMP</strong>(which stands for Cache_Memory_Page_table).</li>

 <li>All data accesses from instructions are using <strong>virtual addressing</strong></li>

 <li>Both instruction cache and data cache have only one level and your simulator should cover both caches.</li>

 <li>Cache Organization

  <ol>

   <li>Both instruction cache and data cache adopt <strong>write-back/allocate</strong></li>

   <li>The cache miss replacement policy for both caches: for the cache line under consideration, replace the <strong>least indexed invalid</strong> set if exists; otherwise, replace the <strong>Bits</strong>–<strong>Pseudo LRU</strong> Details of Bits-Pseudo LRU can be found in Appendix E.</li>

  </ol></li>

</ol>

<ul>

 <li>The <strong>default </strong>instruction cache is of<strong> 16 bytes</strong>,<strong> 4-way associative</strong>. The <strong>block size </strong>for <strong>instruction cache </strong>is<strong> 4 bytes</strong>.</li>

</ul>

<ol>

 <li>The<strong> default</strong> data cache is of<strong> 16 bytes</strong>, <strong>direct map</strong>. The<strong> block size </strong>for <strong>data cache</strong> is<strong> 4 bytes. </strong></li>

</ol>

<ol>

 <li>Cache Initialization</li>

</ol>

The valid bit of each cache block is set to be false before the simulation starts. All other contents are initialized as “don’t care” (x’s).

<ol>

 <li>TLB Organization

  <ol>

   <li>There should be two TLBs, one for IPageTable and one for DPageTable.</li>

   <li>The TLBs is <strong>fully-associative</strong> and its size is a quarter of the page table size, i.e., #TLB_entries = 1/4*(#page_table_entries).</li>

  </ol></li>

</ol>

<ul>

 <li>TLBs adopt the LRU replacement policy. In other words, replace the least indexed invalid entry if exists; otherwise, replace the LRU entry.</li>

</ul>

<ol>

 <li>TLB Initialization</li>

</ol>

The valid bit of each page table block is initialized to be false before simulation begins. All other contents are “don’t care” (x’s).




<ol>

 <li>Page Table Organization</li>

 <li>Although theoretically we should have page table cover full 32-bit virtual space, for simplicity of verification you are required to calculate the page table size from the given disk size specified in this project, i.e., #page_table_entries = disk_size / page_size.</li>

 <li>You have to map virtual address (VA) to physical address (PA)</li>

</ol>

<ul>

 <li>At page fault, we assume that the virtual address (VA) is exactly the disk address.</li>

</ul>

<ol>

 <li>The <strong>default instruction page</strong> size is <strong>8 bytes </strong>and the <strong>default</strong> <strong>data page</strong> size is <strong>16 bytes</strong>.</li>

</ol>

<ol>

 <li>Page Table Initialization</li>

</ol>

The valid bit of each page table block is initialized to be false before simulation begins. All other contents are “don’t care” (x’s).

<ol>

 <li>Memory Organization

  <ol>

   <li>Both instruction memory and data memory adopt <strong>write-back/allocate</strong></li>

   <li>Memory replacement policy for page faults: If memory space is available, place data to the first available page closest to the page #0; otherwise, replace the <strong>LRU</strong> Pick the <strong>least indexed</strong> set to be the victim in case of tie.</li>

  </ol></li>

</ol>

<ul>

 <li>The <strong>default instruction memory</strong> size is of <strong>64 bytes </strong>and the <strong>default data memory</strong> size is of <strong>32 bytes.</strong></li>

</ul>

<ol>

 <li>Memory Initialization</li>

</ol>

All         initial              memory          contents          are       0x00000000<sub>h</sub>.

<ol>

 <li>Disk Initialization

  <ol>

   <li>Assume    that     both    the       instruction     disk     and     data     disk     are       of         <strong>1K       bytes              size</strong>.</li>

   <li>All    other    memory          contents          whose             addresses       not       specified         by        the       image              file         are       assumed         to         be        of         value    0x00000000<sub>h</sub>.</li>

  </ol></li>

 <li>Configurability</li>

</ol>

The executable takes arguments from the command line. <strong>All size related parameters should be of </strong><strong>power of two, and the exponent should be great than 1 (2<sup>n</sup>, n &gt; 1). </strong>Note that if no command line parameters are set, the default configuration is taken for simulation. Other specifications are the same as <em>project_1.pdf</em>. The parameters should be of the following order:

<ol>

 <li>The instruction memory (I memory) size, in number of bytes</li>

 <li>The data memory (D memory) size, in number of bytes</li>

</ol>

<ul>

 <li>The page size of instruction memory (I memory), in number of bytes</li>

</ul>

<ol>

 <li>The page size of data memory (D memory), in number of bytes v.            The total size of instruction cache (I cache), in number of bytes</li>

 <li>The block size of I cache, in number of bytes vii.     The set associativity of I cache

  <ul>

   <li>The total size of data cache (D cache), in number of bytes</li>

  </ul></li>

</ol>

<ol>

 <li>The block size of D cache, in number of bytes</li>

 <li>The set associativity of D cache</li>

</ol>




<ol start="3">

 <li>Input and Output Format</li>

</ol>

Input: Same as that of Project 1. Please refer to the specification of Project 1 and <em>Appendix B</em>, “<em>Sample Input</em>.”

Output: For each test case, <strong>report.rpt</strong> and <strong>snapshot.rpt</strong> should be generated.  a.   <strong>snapshot.rpt</strong>

The requirement is the same as that for project 1. Please refer to <em>project_1 </em>and <em>Appendix C-1</em>,

“<em>Sample Output for Project 1</em>.”

<ol>

 <li><strong>report.rpt: </strong>

  <ul>

   <li>For details please refer to <em>Appendix C-3</em>, “<em>Sample Output for Project 3</em>.”</li>

   <li>rpt should contain the following information for total memory access: total hit /miss number of I-cache, D-cache, I-pagetable, D-pagetable, I-TLB, D-TLB.</li>

  </ul></li>

</ol>




<ol start="4">

 <li>Test Case Design

  <ol>

   <li>Design a test case for the default configuration or other legal configuration to verify if your simulator handles every cache event correctly.</li>

   <li>The following testcases are <strong>invalid</strong>:

    <ol>

     <li>i-memory &amp; d-memory address overflow</li>

     <li>i-memory &amp; d-memory misaligned</li>

    </ol></li>

  </ol></li>

</ol>

<ul>

 <li>Simulation cycles over 500,000</li>

</ul>




<ol start="5">

 <li>Modularization</li>

</ol>

On top of the same design of Project 1, you can add a file named as cmp.c to implement your cache, TLB, page table related functions.




<ol start="6">

 <li>Grading Policy

  <ol>

   <li>Mostly are same as Project 1, with each testcase (open, hidden, student testcase) testing with <strong>three different configurations</strong>: default configuration and two other configurations. i.        10% discount if you fail one of them

    <ol>

     <li>19% discount if you fail both of them</li>

    </ol></li>

  </ol></li>

</ol>

<ul>

 <li>0 point if you fail all of them</li>

</ul>

<ol>

 <li>Demo will focus on:

  <ol>

   <li>Detail design of your program</li>

   <li>Basic organization of TLB, page table, and memory iii.      Project report</li>

  </ol></li>

</ol>




<ol start="7">

 <li><strong>Etiquette </strong>

  <ol>

   <li><strong>Do not plagiarize others’ works, or you will fail this course. </strong></li>

   <li><strong>No acceptance of late homework. </strong></li>

   <li><strong>Please constantly check the class website announcements for any possible updates. </strong></li>

  </ol></li>

</ol>


