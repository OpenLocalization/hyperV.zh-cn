#Step 4: Create a Windows virtual machine from an .iso file

For this step, if you already have a .iso file for a supported 64-bit operating system, you can use that.
If not, you can download the .iso for [Windows 8.1 Enterprise](http://www.microsoft.com/en-us/evalcenter/evaluate-windows-8-1-enterprise) and choose the 64-bit edition.

1.  In Hyper-V Manager, click on the **Action** menu > **New** > **Virtual machine**.
2.  In the virtual machine wizard, make the following choices:
    
    <table>
      <tr>
        <th caps_internal_Id="186f378c-c878-46a6-ad3d-109d3a044adc">Page</th>
        <th caps_internal_Id="d012c845-2465-486a-835c-b7145cb2c12c">Entry</th>
      </tr>
      <tr>
        <td caps_internal_Id="8f780090-0f0d-40ca-af05-c7ac7b12ac8f">Name:</td>
        <td>Type in <b caps_internal_Id="734f0e65-01b2-452a-b3d3-34086906048a">Windows Walkthrough VM</b></td>
      </tr>
      <tr>
        <td caps_internal_Id="2e1e0942-3162-4c72-963c-1815a7b3bc0b">Generation:</td>
        <td>
          <b caps_internal_Id="55c82fda-c892-4f81-9dfc-31901a12c25e">Generation 2</b>
        </td>
      </tr>
      <tr>
        <td caps_internal_Id="2cac8ce5-81ec-4ed4-b64c-6474cda583ae">Startup Memory:</td>
        <td>
          <b caps_internal_Id="1a534b1c-c662-4e65-81fe-699f7b9e5f24">1024</b> and leave dynamic memory selected</td>
      </tr>
      <tr>
        <td caps_internal_Id="0e30b71f-d1d6-49d4-a9ba-da81f6ea2c89">Configure Networking:</td>
        <td>
          <b caps_internal_Id="3e76a5c4-2a70-4137-a65b-b097ce06616b">External</b> (this is the virtual switch you created in Step 3)</td>
      </tr>
      <tr>
        <td caps_internal_Id="6736b9bb-ae3f-48c2-b07c-6cb8ba05c999">Connect virtual hard disk:</td>
        <td>
          <b caps_internal_Id="1791c643-8ebd-4f97-af92-6037ef35fe30">Create a virtual hard disk</b> (keep the other default values) </td>
      </tr>
      <tr>
        <td caps_internal_Id="816e59c2-5f86-4e84-8d58-ccd6dd37d7e3">Installation Options:</td>
        <td>
          <b caps_internal_Id="9ce1a6c0-758b-4de2-9b9d-8dd4c5c9364d">Install an operating system from a bootable CD/DVD-ROM</b>. Under <b caps_internal_Id="81979dc7-72e3-4fa7-969c-edb4fb162000">Media</b>, select <b caps_internal_Id="10033a9f-5814-44bd-b74e-44d600f0e6e5">Image file (iso)</b> and then click <b caps_internal_Id="26db4d2d-7e80-46a0-8666-b33011995141">Browse</b> to point to the .iso file.</td>
      </tr>
    </table>
3.  When everything looks right, click **Finish**.

> **Note:** If you only have 32-bit version of Windows, you need to choose Generation 1 in the **Generation** section of the wizard.
> Generation 2 VMs only support 64-bit operating systems.
> 

##Next Step:

[Step 5: Connect to the virtual machine and finish the installation](walkthrough_vmconnect.md)


