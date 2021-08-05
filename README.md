# Custom HellsGate Implementation
Assembly HellGate implementation that directly calls Windows System Calls and displays the PPID of the explorer.exe process.

![](/images/customHellsGatePoC.png)
+ In this screenshot the "NtQuerySystemInformation" & "NtAllocateVirtualMemory" NTDLL.DLL API's are called by direct windows system calls.
+ The systemcalls are dynamically discovered at runtime using the HellsGate method.
+ This method avoids EDR userland hooks.

### Things I am aware of / To Do List
+ Obfuscate the strings for that are used for resolving the addresses of the NTDLL symbols
  + Or use hashing
+ Need to fix some bugs when switching from debug to release mode in visual studio's
+ Need to figure out how to properly overload the call to HellDescent()
+ Clean up the assembly functions, they are messy and could be better
+ Do better checking for the process image name so it doesnt conflict with other processes named explorer*
+ Better error handling
+ Make this into a cobalt strike beacon object file
+ Build on this project for process injection / syscall PS 

### Credits / References
+ Pavel Yosifovich (@zodiacon)
  + I learned how to correctly call NtQuerySystemInformation from Pavel's class on pentester academy. Full credits to Pavel for this. (BTW Pavel is an awesome teacher and I 100% recommend).
  + [Windows Process Injection for Red-Blue Teams - Module 2: NTQuerySystemInformation](https://www.pentesteracademy.com/video?id=1634)
+ Reenz0h from @SEKTOR7net
  + Most of the C techniques I use are from Reenz0h's awesome courses and blogs 
  + https://blog.sektor7.net/#!res/2021/halosgate.md 
  + https://institute.sektor7.net/
+ @smelly__vx & @am0nsec ( Creators/Publishers of the Hells Gate technique )
  + Could not have made my implementation of HellsGate without them :)
  + Awesome work on this method, really enjoyed working through it myself. Thank you!
  + https://github.com/am0nsec/HellsGate 
  + Link to the Hell's Gate paper: https://vxug.fakedoma.in/papers/VXUG/Exclusive/HellsGate.pdf
