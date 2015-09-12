#什么是新超 v 上 Windows 10

本主题说明在 Windows 10 ® HYPER-V 中的新的和更改的功能。
这是用于测试。

##Windows PowerShell 直接

还有现在简便可靠的方法从主机操作系统运行在虚拟机中的 Windows PowerShell 命令。
没有网络或防火墙的要求，也没有特殊的配置。
无论您的远程管理配置，它正常工作。
若要使用它，必须在主机和虚拟机来宾操作系统上运行 Windows 10 或 Windows 服务器技术预览版。

若要创建 PowerShell 直接会话，请使用以下命令之一:

``` PowerShell
Enter-PSSession -VMName VMName
Invoke-Command -VMName VMName -ScriptBlock { commands }


```

Today, Hyper-V administrators rely on two categories of tools for connecting to a virtual machine on their Hyper-V host:
- Remote management tools such as PowerShell or Remote Desktop
- Hyper-V Virtual Machine Connection (VM Connect)

Both of these technologies work well, but each have trade-offs as your Hyper-V deployment grows. VMConnect is reliable, but it can be hard to automate. Remote PowerShell is powerful, but can be difficult to setup and maintain. 

Windows PowerShell Direct provides a powerful scripting and automation experience with the simplicity of VMConnect. Because Windows PowerShell Direct runs between the host and virtual machine, there is no need for a network connection or to enable remote management. You do need guest credentials to log into the virtual machine.

#### Requirements
- You must be connected to a Windows 10 or Windows Server Technical Preview host with virtual machines that run Windows 10 or Windows Server Technical Preview as guests.
- You need to be logged in with Hyper-V Administrator credentials on the host.
- You need User credentials for the virtual machine.
- The virtual machine you want to connect to must be running and booted.


## Hot add and remove for network adapters and memory

You can now add or remove a Network Adapter while the virtual machine is running, without downtime. This works for generation 2 virtual machines running both Windows and Linux operating systems. 

You can also adjust the amount of memory assigned to a virtual machine while it's running, even if you haven’t enabled Dynamic Memory. This works for both generation 1 and generation 2 virtual machines.

## Production checkpoints

Production checkpoints allow you to easily create “point in time” images of a virtual machine, which can be restored later on in a way that is completely supported for all production workloads. This is achieved by using backup technology inside the guest to create the checkpoint, instead of using saved state technology. For production checkpoints, the Volume Snapshot Service (VSS) is used inside Windows virtual machines. Linux virtual machines flush their file system buffers to create a file system consistent checkpoint. If you want to create checkpoints using saved state technology, you can still choose to use standard checkpoints for your virtual machine. 


> **Important:** The default for new virtual machines will be to create production checkpoints with a fallback to standard checkpoints. 


## Hyper-V Manager improvements

- **Alternate credentials support** – You can now use a different set of credentials in Hyper-V manager when you connect to another Windows 10 Technical Preview remote host. You can also save these credentials so it's easier to log on later. 

- **Down-level management** - You can now use Hyper-V manager to manage more versions of Hyper-V. With Hyper-V manager in Windows 10 Technical Preview, you can manage computers running Hyper-V on Windows Server 2012, Windows 8, Windows Server 2012 R2 and Windows 8.1.

- **Updated management protocol** - Hyper-V manager has been updated to communicate with remote Hyper-V hosts using the WS-MAN protocol, which permits CredSSP, Kerberos or NTLM authentication. When you use CredSSP to connect to a remote Hyper-V host, it allows you to perform a live migration without first enabling constrained delegation in Active Directory. WS-MAN-based infrastructure also simplifies the configuration necessary to enable a host for remote management. WS-MAN connects over port 80, which is open by default.


## Connected Standby works 

When Hyper-V is enabled on a computer that uses the Always On/Always Connected (AOAC) power model, the Connected Standby power state is now available.

In Windows 8 and 8.1, Hyper-V caused computers that used the Always On/Always Connected (AOAC) power model (also known as InstantON) to never sleep. See this [KB article](
https://support.microsoft.com/en-us/kb/2973536) for a full discription.


## Linux secure boot 

More Linux operating systems, running on generation 2 virtual machines, can now boot with the secure boot option enabled.  Ubuntu 14.04 and later, and SUSE Linux Enterprise Server 12, are enabled for secure boot on hosts that run the Technical Preview. Before you boot the virtual machine for the first time, you must specify that the virtual machine should use the Microsoft UEFI Certificate Authority.  At an elevated Windows Powershell prompt, type:

    Set-VMFirmware vmname -SecureBootTemplate MicrosoftUEFICertificateAuthority

For more information on running Linux virtual machines on Hyper-V, see [Linux and FreeBSD Virtual Machines on Hyper-V](http://technet.microsoft.com/library/dn531030.aspx).


## Virtual Machine Configuration Version 

When you move or import a virtual machine to a host running Hyper-V on Windows 10 from host running Windows 8.1, the virtual machine’s configuration file isn't automatically upgraded. This allows the virtual machine to be moved back to a host running Windows 8.1. You won't have access to new virtual machine features until you manually update the virtual machine configuration version. 

The virtual machine configuration version represents what version of Hyper-V the virtual machine’s configuration, saved state, and snapshot files it's compatible with. Virtual machines with configuration version 5 are compatible with Windows 8.1 and can run on both Windows 8.1 and Windows 10. Virtual machines with configuration version 6 are compatible with Windows 10 and won't run on Windows 8.1.

#### How do I check the configuration version of the virtual machines running on Hyper-V? 

From an elevated command prompt, run the following command:

``` PowerShell
Get-VM * | Format-Table Name, Version

```


####如何升级配置版本的虚拟机?

从提升 Windows PowerShell 命令提示符下，运行以下命令之一:

``` PowerShell
Update-VmConfigurationVersion <vmname>


```

Or

``` PowerShell
Update-VmConfigurationVersion <vmobject>

```

** 重要: **

*   您的虚拟机配置版本升级后，你不能将虚拟机移动到运行 Windows 8.1 的主机。
*   您不能降级版本 6 到版本 5 的虚拟机配置版本。
*   您必须先关闭虚拟机升级虚拟机的配置。
*   升级之后，虚拟机使用新的配置文件格式。
    更多的信息，请参阅新虚拟机配置文件格式。

##新的虚拟机配置文件格式

虚拟机现在有新的配置文件格式，旨在提高阅读和写作的虚拟机配置数据的效率。
它同时也被为了减少潜在的数据损坏，如果存储故障。
新的配置文件使用。VMCX 扩展为虚拟机配置数据和。运行时状态数据的 VMRS 扩展名。

> **重要:**了。VMCX 文件是二进制的格式。
> 直接编辑。VMCX 或。VMRS 文件不受支持。
> 

##通过 Windows Update 提供一体化服务

集成服务为 Windows 客人的更新现在分布通过 Windows 更新。

集成组件 (也称为集成服务) 是合成的驱动程序，允许虚拟机与主机操作系统进行通信的一组。
他们控制从时间同步到客人文件复制服务。
我们已经谈过客户集成组件的安装和更新在过去一年来发现他们在升级过程中都是一个巨大的痛点。

从历史上看，所有新版本的 HYPER-V 附带新的集成组件。
升级 HYPER-V 主机升级集成组件在虚拟机以及必需。
新的集成组件都包含在 HYPER-V 主机，然后他们在使用 vmguest.iso 的虚拟机中安装了。
这个过程需要重新启动虚拟机，不能与其他 Windows 更新批处理。
因为 HYPER-V 管理员必须提供 vmguest.iso 和虚拟机管理员不得不安装它们，集成组件升级所需的 HYPER-V 管理员具有管理员凭据在虚拟机 — — 这并非总是如此。

在 Windows 10 和前进，所有集成组件将交付给虚拟加工通过 Windows 更新和其他重要更新。

有可用更新今天为运行的虚拟机:

*   Windows 服务器 2012
*   Windows 服务器 2008 R2
*   Windows 8
*   Windows 7

虚拟机必须连接到 Windows Update 或 WSUS 服务器。
在将来，集成组件更新将有一个类别 ID，对于此版本，他们被列为 KBs。

阅读更多有关我们如何确定适用性，看看这[博客文章](http://blogs.technet.com/b/virtualization/archive/2014/11/24/integration-components-how-we-determine-windows-update-applicability.aspx).

请参见[这个博客](http://blogs.msdn.com/b/virtual_pc_guy/archive/2014/11/12/updating-integration-components-over-windows-update.aspx)有关详细的安装集成服务演练的职位。

> **重要:**ISO 图像文件 vmguest.iso 不再需要更新集成组件。
> 它不包括在 HYPER-V 上 Windows 10。
> 

##下一步

[在 Windows 上 10 走过超 V](..\quick_start\walkthrough.md)


s KBs.

To read more about how we determine applicability, see this [blog post](http://blogs.technet.com/b/virtualization/archive/2014/11/24/integration-components-how-we-determine-windows-update-applicability.aspx).


See [this blog](http://blogs.msdn.com/b/virtual_pc_guy/archive/2014/11/12/updating-integration-components-over-windows-update.aspx) post for a detailed walkthrough of installing integration services.


> **Important:** The ISO image file vmguest.iso is no longer needed for updating integration components. It's not included with Hyper-V on Windows 10.




## Next Step
[Walk through Hyper-V on Windows 10](..\quick_start\walkthrough.md) 