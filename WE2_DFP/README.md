How to run WE2 example ?
 Requirement:
  a. Keil MDK μVision (v5.38 is tested)
  b. pyOCD (v0.34.3 is tested)
  c. CMSIS-DAP Compatible Debugger

 1. Install Keil MDK μVision
 2. Double click Himax.WE2_DFP.1.0.3.pack to install pack using Keil Pack Unzip
 3. Open Keil uVision menu bar select 'Project -> Manage -> Pack Installer'
 4. Switch to 'Devices' and 'Examples' tabpages
 5. Select Himax in Devices tabpage
 6. In 'Examples' tabpage, double click [WLCP65][MDK]hello_world_tz 'Copy' button 
 7. Select destination path (D:\mdk_test) and click "Use Pack Folder Structure" in Dialog.
    The example will copy to D:\mdk_test\WE2_Ex\WLCSP65\MDK\hello_world_tz
 8. Open path D:\mdk_test\WE2_Ex\WLCSP65\MDK\hello_world_tz\hello_world_tz.uvmpw
     Keil menu bar select 'Project -> Batch Build' to build hello_world_tz
 	The two elf files, we2_cm55m_ns_app.elf and we2_cm55m_s_app.elf, will be generated.
 9. Download image_gen tool https://github.com/HimaxWiseEyePlus/cmsis-packs/tree/main/WE2_DFP/tool.7z
 10. Unzip tool to D:\mdk_test\WE2_Ex\WLCSP65\MDK\hello_world_tz
 11. Run gen_image_mdk.bat to merage elf files and WE2 bootloader
     The complete image (output.img) will be generated in 
 	D:\mdk_test\WE2_Ex\WLCSP65\MDK\hello_world_tz\tool\we2_image_gen_local_exe_release_177231\output\
 12. Run swd_progamming_flash.bat to progam WE2 external NOR flash via SWD interface using pyOCD CMSIS-DAP
 13. HW Reset WE2 board

How to run debugging in Keil ?
 Requirement:
  a. Keil MDK μVision (v5.38 is tested)
  b. CMSIS-DAP Compatible Debugger

 1. set we2_cm55m_s_app as active project
 2. select Option for Target 'we2_cm55m_s_app'
 3. select CMSIS-DAP ARMv8-M Debugger for Debug item
 4. Keil uVision menu bar select 'Debug -> Start/Stop Debug Session'
