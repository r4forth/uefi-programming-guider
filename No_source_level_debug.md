# 问题：调试时不能正确加载调试符号 #
书中讲到了如何利用`_asm int 3 `调试代码。<br>
<code>_asm int 3</code>需要配合<code>Nt32Pkg</code>使用。也就是说通过<code>Nt32Pkg</code>编译出的.efi文件才能够调试。<br><br>
如果你带<code>_asm int 3</code>语句的工程是通过非<code>Nt32Pkg</code>编译出来的（例如<code>AppPkg</code>），在<code>SecMain</code>模拟器中调试会导致断点停在Image.c文件如下代码中<br>
<pre><code>Image-&gt;Status = Image-&gt;EntryPoint (ImageHandle, Image-&gt;Info.SystemTable);<br>
</code></pre>
同时在模拟器控制台你会看到<br>
<code> WARNING: No source level debug</code>

<h1>解决方案</h1>

在.inf文件中添加如下代码<br>
<pre><code>[BuildOptions]<br>
  MSFT:DEBUG_*_IA32_DLINK_FLAGS = /EXPORT:InitializeDriver=$(IMAGE_ENTRY_POINT) /ALIGN:4096 /FILEALIGN:4096 /SUBSYSTEM:CONSOLE<br>
</code></pre>