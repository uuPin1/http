# PowerShell for Scientific Computation
>这篇笔记将帮助你完成powershell的基本配置，尤其是针对使用python3科学计算的相关组件。

---
## 配置的第一步
>>1. 以管理员身份进入powershell  
2. 设置你的用户权限  
   `PS> Set-ExecutionPolicy RemoteSigned -Force`  
More about [ExecutionPolicy](https://technet.microsoft.com/zh-CN/library/hh847748.aspx) 

## 配置好看好用的Shell I - $profile Build  
>More about [$profile 设置](https://msdn.microsoft.com/en-us/library/bb613488)

## 配置好看好用的Shell II - ConEmu
>>1. 安装chocolatey - 文件管理  
   `PS> iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex`  
p.s. iwr这个命令从属于PacketManagement，如果提示没有这个命令，建议逐次安装升级你的powerShell，每次可以使用`$env:PSModulePath -split ';' | % { dir $_ } | % { $_.Name }`查看你的PowerShell是否含有这个组件
More about [PackeageManagement disappear](https://github.com/OneGet/oneget/issues/148)  
2. 安装chocolatey组件  
   `choco install conemu -y`  
   `choco install python3 -y`  
   `choco install git.install -y`  
3. 配置ConEmu - 窗口管理  
   Appearance - Single instance mode(enable)  
   Quake style - Quake style slide down(enable)  
   Startup - Specified named task{Shells::PowerShell}  
   Key & Macro - hotkey for Minimize/Restore  
More about [ConEmu & Github](https://hodgkins.io/ultimate-powershell-prompt-and-git-setup)

## python3 pip - numpy, scipy, pandas, matplotlib, ...
>我们在完成python3安装(`choco install python3 -y`)之后，就可以进行这一步操作。python2可同理完成，但我没有进行测试。如果装有两个版本，请设置好环境变量，保证python pip对应的版本。  
>>1. 安装pip  
   `python -m pip install --update pip`  
2. 安装numpy, scipy  
   `pip install "./.../numpy+mkl.whl"`  
   download site:[numpy+mkl](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy)  
   `pip install "./.../scipy.whl"`  
   download site:[scipy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy)  
   p.s. 必须首先安装numpy，再安装scipy。由于Windows中不含有lapack/blas，所以不能仅仅安装numpy，必须还需安装numpy+mkl  
More about [this question](http://stackoverflow.com/questions/28190534/windows-scipy-install-no-lapack-blas-resources-found)  
3. 安装其他的python包  
   `pip install matplotlib`  
   `pip install pandas`  
   ...  
   `pip install ipython`  
   `pip install jupyter`  *for ipython- notebook*  

## SSH
>系统及配置要求：Win10 或者 WMF5.0  
>>1. 找到posh-SSH并安装  
   `Find-Module PoSH-SSH | Install-Module`  
2. SSH cmdlets  
   `Get-Command -Module PoSH-SSH`  
3. New a SSH Session  
   `New-SSHSection -ComputerName IP/"Website" -Credential (Get-Gredential)`  

>another way: [Using Chocolatey-putty](https://cmatskas.com/run-ssh-with-powershell/)

## Subsystem for Ubuntu
>way: [Xming + Win10-BashShell](http://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/)  
tool: [CERN-ROOT for Subsystem](https://medium.com/@blake.leverington/installing-cern-root-under-windows-10-with-subsystem-for-linux-beta-75295defc6d4#.xxh9g6klq)
