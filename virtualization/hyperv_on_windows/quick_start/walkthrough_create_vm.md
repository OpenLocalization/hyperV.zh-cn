ms.ContentId: 3C63F9A8-30E4-40F4-BC7B-A001C1E90779
title: Step 4: Create a Windows virtual machine from an .iso file

#Step 4: Create a Windows virtual machine from an .iso file

For this step, if you already have a .iso file for a supported 64-bit operating system, you can use that.
If not, you can download the .iso for [Windows 8.1 Enterprise](http://www.microsoft.com/en-us/evalcenter/evaluate-windows-8-1-enterprise) and choose the 64-bit edition.

1.  In Hyper-V Manager, click on the **Action** menu > **New** > **Virtual machine**.
2.  In the virtual machine wizard, make the following choices:
    
    <table>
      <tr>
        <th caps_internal_Id="e2eca143-af72-4c00-906e-99368f77083d">Page</th>
        <th caps_internal_Id="7373383b-19a6-4a37-be1e-b09950e047a8">Entry</th>
      </tr>
      <tr>
        <td caps_internal_Id="72b20ad2-53e6-405a-8943-5fcb368244f8">Name:</td>
        <td>Type in <b caps_internal_Id="0ea235a1-291b-4852-b0fc-f79f0786c443">Windows Walkthrough VM</b></td>
      </tr>
      <tr>
        <td caps_internal_Id="c84554ee-c7c3-4c2e-8094-088a71bdc5fc">Generation:</td>
        <td>
          <b caps_internal_Id="9796de79-d3fc-4352-997f-ed481e68088b">Generation 2</b>
        </td>
      </tr>
      <tr>
        <td caps_internal_Id="46b84865-61d0-44b5-a7ba-a7bcc36fd0e1">Startup Memory:</td>
        <td>
          <b caps_internal_Id="b8de6c30-0280-4da4-8db6-b4b5019582f6">1024</b> and leave dynamic memory selected</td>
      </tr>
      <tr>
        <td caps_internal_Id="9cf7e733-2b26-4f93-a988-f8bb38b52b5d">Configure Networking:</td>
        <td>
          <b caps_internal_Id="0181f60e-6040-4de8-900b-5af86647e7c5">External</b> (this is the virtual switch you created in Step 3)</td>
      </tr>
      <tr>
        <td caps_internal_Id="b3fb709c-aa32-41ce-a443-e58fe7e8d94a">Connect virtual hard disk:</td>
        <td>
          <b caps_internal_Id="9f45e5c1-640a-4a8e-b97c-4b70f7e46e27">Create a virtual hard disk</b> (keep the other default values) </td>
      </tr>
      <tr>
        <td caps_internal_Id="f3dc0ac3-e3fc-423e-ab0d-83910b4c20b3">Installation Options:</td>
        <td>
          <b caps_internal_Id="424fa00f-d2fc-42be-80ef-ac66d8555663">Install an operating system from a bootable CD/DVD-ROM</b>. Under <b caps_internal_Id="71e9f451-4706-4e10-9b07-c16604ea2384">Media</b>, select <b caps_internal_Id="23be66b8-7283-41c0-bf1f-ff9ee89c38a5">Image file (iso)</b> and then click <b caps_internal_Id="29de4e0d-faf6-4499-ac80-acb9a1d604b5">Browse</b> to point to the .iso file.</td>
      </tr>
    </table>
3.  When everything looks right, click **Finish**.

> **Note:** If you only have 32-bit version of Windows, you need to choose Generation 1 in the **Generation** section of the wizard.
> Generation 2 VMs only support 64-bit operating systems.
> 

##Next Step:

[Step 5: Connect to the virtual machine and finish the installation](walkthrough_vmconnect.md)


