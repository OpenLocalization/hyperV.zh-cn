ms.ContentId: 3C63F9A8-30E4-40F4-BC7B-A001C1E90779
title: Step 4: Create a Windows virtual machine from an .iso file

#Step 4: Create a Windows virtual machine from an .iso file

For this step, if you already have a .iso file for a supported 64-bit operating system, you can use that.
If not, you can download the .iso for [Windows 8.1 Enterprise](http://www.microsoft.com/en-us/evalcenter/evaluate-windows-8-1-enterprise) and choose the 64-bit edition.

1.  In Hyper-V Manager, click on the **Action** menu > **New** > **Virtual machine**.
2.  In the virtual machine wizard, make the following choices:
    
    <table>
      <tr>
        <th caps_internal_Id="ecc44c3e-4d02-44de-9305-8bdb5b37c0e7">Page</th>
        <th caps_internal_Id="1a3c728e-9fcc-4602-87c4-19b1bee2edb3">Entry</th>
      </tr>
      <tr>
        <td caps_internal_Id="d83fc6db-508e-4aa6-ba5c-6690d6e03d6d">Name:</td>
        <td>Type in <b caps_internal_Id="e2ea6566-2fbe-45f2-833c-73413d6604ae">Windows Walkthrough VM</b></td>
      </tr>
      <tr>
        <td caps_internal_Id="d010d8f6-f2e9-49cc-a9ce-18f6ec171d45">Generation:</td>
        <td>
          <b caps_internal_Id="ac14e96a-4b88-4f9c-89e0-7faf4243d5ee">Generation 2</b>
        </td>
      </tr>
      <tr>
        <td caps_internal_Id="1e527121-93b1-4975-8e34-8155069d7916">Startup Memory:</td>
        <td>
          <b caps_internal_Id="9a0ef89e-9c97-4ee1-9c92-593f5b162a4c">1024</b> and leave dynamic memory selected</td>
      </tr>
      <tr>
        <td caps_internal_Id="d87e2bd6-8288-44f3-ae7a-9d9524032983">Configure Networking:</td>
        <td>
          <b caps_internal_Id="bac2b371-85d2-46d3-b87f-4e4819174e1a">External</b> (this is the virtual switch you created in Step 3)</td>
      </tr>
      <tr>
        <td caps_internal_Id="2a3d4659-68c7-4708-8e56-53c63037f7e0">Connect virtual hard disk:</td>
        <td>
          <b caps_internal_Id="c373c85e-6f44-4e0c-8b89-87d43c53d3af">Create a virtual hard disk</b> (keep the other default values) </td>
      </tr>
      <tr>
        <td caps_internal_Id="3384fe83-e240-45df-8b05-b0cd5503ba69">Installation Options:</td>
        <td>
          <b caps_internal_Id="2c072a99-5e34-4c08-ad11-3f882cfb44f0">Install an operating system from a bootable CD/DVD-ROM</b>. Under <b caps_internal_Id="dead6544-3006-4ca9-9405-a0877caf7677">Media</b>, select <b caps_internal_Id="04c57560-187d-4f9c-88ad-8fbee61d006a">Image file (iso)</b> and then click <b caps_internal_Id="bbf97948-33c1-410f-af5b-91b8aee43328">Browse</b> to point to the .iso file.</td>
      </tr>
    </table>
3.  When everything looks right, click **Finish**.

> **Note:** If you only have 32-bit version of Windows, you need to choose Generation 1 in the **Generation** section of the wizard.
> Generation 2 VMs only support 64-bit operating systems.
> 

##Next Step:

[Step 5: Connect to the virtual machine and finish the installation](walkthrough_vmconnect.md)


