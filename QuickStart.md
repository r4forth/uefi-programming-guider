# 编译源代码的步骤： #

### EDK2源代码版本号为13087 ###
  * 下载EDK2源代码
    * svn co https://svn.code.sf.net/p/edk2/code/trunk/edk2 -r 13087
  * 在EDK2根目录下建立uefi目录。
  * 将文件夹book复制到uefi目录。
  * 打开CMD命令行
  * 在命令行切换到EDK2根目录
  * 在命令行执行
    * ` edksetup.bat --nt32`
  * 在命令行执行
    * ` build -p uefi\book\Nt32Pkg\Nt32Pkg.dsc `
    * ` build -p uefi\book\AppPkg\AppPkg.dsc `
  * 把`StdLib\Include\sys\EfiCdefs.h`第330行注释掉
> > ` #ifdef _NATIVE_WCHAR_T_DEFINED`<br>
<blockquote><code>//  #error You must specify /Zc:wchar_t- to the compiler to turn off intrinsic nwchar_t.</code><br>
<code> #endif</code><br>
</blockquote><ul><li>在命令行执行<br>
<ul><li><code> build -p uefi\book\GUIPkg\GUIPkg.dsc </code></li></ul></li></ul>

<h3>UDK2014</h3>

<ul><li>在EDK2根目录下建立uefi目录。<br>
</li><li>将文件夹book复制到uefi目录。<br>
</li><li>打开CMD命令行<br>
</li><li>在命令行切换到EDK2根目录<br>
</li><li>在命令行执行<br>
<ul><li><code> edksetup.bat --nt32</code>
</li></ul></li><li>将<code>uefi\book\Nt32Pkg\Nt32Pkg.inc</code>文件添加到<code>Nt32Pkg\Nt32Pkg.dsc</code>末尾<br>
<ul><li><code>type uefi\book\Nt32Pkg\Nt32Pkg.inc &gt;&gt; Nt32Pkg\Nt32Pkg.dsc</code>
</li></ul></li><li>在命令行执行<br>
<ul><li><code> build </code></li></ul></li></ul>

<h3>EDK2源代码版本号为16682</h3>
<ul><li>下载EDK2源代码<br>
<ul><li>svn co <a href='https://svn.code.sf.net/p/edk2/code/trunk/edk2'>https://svn.code.sf.net/p/edk2/code/trunk/edk2</a> -r 16682<br>
</li></ul></li><li>在EDK2根目录下建立uefi目录。<br>
</li><li>将文件夹book复制到uefi目录。<br>
</li><li>打开CMD命令行<br>
</li><li>在命令行切换到EDK2根目录<br>
</li><li>在命令行执行<br>
<ul><li><code> edksetup.bat --nt32</code>
</li></ul></li><li>把<code>StdLib\Include\sys\EfiCdefs.h</code>第330行注释掉<br>
<blockquote><code> #ifdef _NATIVE_WCHAR_T_DEFINED</code><br>
<code>//  #error You must specify /Zc:wchar_t- to the compiler to turn off intrinsic nwchar_t.</code><br>
<code> #endif</code><br>
</blockquote></li><li>编译<code>Nt32Pkg</code>
<ul><li>将<code>uefi\book\Nt32Pkg\Nt32Pkg-2.4.inc</code>文件添加到<code>Nt32Pkg\Nt32Pkg.dsc</code>末尾<br>
<ul><li><code>type uefi\book\Nt32Pkg\Nt32Pkg-2.4.inc &gt;&gt; Nt32Pkg\Nt32Pkg.dsc</code>
</li></ul></li><li>在命令行执行<br>
<ul><li><code> build -p Nt32Pkg\Nt32Pkg.dsc</code>
</li></ul></li></ul></li><li>编译<code>AppPkg</code>
<ul><li>将<code>uefi\book\AppPkg\AppPkg-2.4.inc</code>文件添加到<code>AppPkg\AppPkg.dsc</code>末尾<br>
<ul><li><code>type uefi\book\AppPkg\AppPkg-2.4.inc &gt;&gt; AppPkg\AppPkg.dsc</code>
</li><li><code> build -p AppPkg\AppPkg.dsc</code>