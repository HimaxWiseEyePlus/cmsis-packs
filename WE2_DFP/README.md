# How to run WE2 Keil example ?
 
 - Requirement:
     - a. Keil MDK μVision (v5.38 is tested)
     - b. pyOCD (v0.34.3 is tested, see 'How to install pyOCD ?') or pyOCD_HX (see 'How to install pyOCD_HX ?')
     - c. CMSIS-DAP Compatible Debugger

 1. Install Keil MDK μVision
 2. Double click Himax.WE2_DFP.1.0.0.pack to install pack using Keil Pack Unzip
 3. Open Keil uVision menu bar select 'Project -> Manage -> Pack Installer'
 4. Switch to 'Devices' and 'Examples' tabpages
 5. Select Himax in Devices tabpage
 6. In 'Examples' tabpage, double click [WLCP65][MDK]hello_world_tz 'Copy' button 
 7. Select destination path (D:\mdk_test) and click "Use Pack Folder Structure" in Dialog.
    The example will copy to D:\mdk_test\WE2_Ex\WLCSP65\MDK\hello_world_tz
 8. Open path D:\mdk_test\WE2_Ex\WLCSP65\MDK\hello_world_tz\hello_world_tz.uvmpw
     Keil menu bar select 'Project -> Batch Build' to build hello_world_tz
 	The two elf files, we2_cm55m_ns_app.elf and we2_cm55m_s_app.elf, will be generated.
 9. Download image_gen tool https://github.com/HimaxWiseEyePlus/cmsis-packs/raw/main/WE2_DFP/tool.7z
 10. Unzip tool to D:\mdk_test\WE2_Ex\WLCSP65\MDK\hello_world_tz
 11. Run gen_image_mdk.bat to merage elf files and WE2 bootloader
     The complete image (output.img) will be generated in 
 	D:\mdk_test\WE2_Ex\WLCSP65\MDK\hello_world_tz\tool\we2_image_gen_local_exe_release_177231\output\
 12. Run swd_progamming_flash.bat to progam WE2 external NOR flash via SWD interface using pyOCD CMSIS-DAP
 13. HW Reset WE2 board

# How to run debugging in Keil ?
 - Requirement:
      - a. Keil MDK μVision (v5.38 is tested)
      - b. CMSIS-DAP Compatible Debugger

 1. set we2_cm55m_s_app as active project
 2. select Option for Target 'we2_cm55m_s_app'
 3. select CMSIS-DAP ARMv8-M Debugger for Debug item
 4. Keil uVision menu bar select 'Debug -> Start/Stop Debug Session'

# How to run WE2 VS Code Arm CMSIS csolution example ?
 - Requirement:
      - a. VS Code (v1.81.1 is tested)
      - b. VS Code Extension
           - Arm.cmsis-csolution (v1.5.2 is tested)
           - Arm.environment-manager (v1.0.5 is tested):
               toolchain for cmake, ninja, armclang, cmsis-toolbox and arm-none-eabi-gcc
      - c. pyOCD_HX (see 'How to install pyOCD_HX ?')
      - d. cmsis-toolbox v2.0.0
      - e. CMSIS-DAP Compatible Debugger (https://pyocd.io/docs/debug_probes.html)

 1. Install VS Code (https://code.visualstudio.com/download) 
 2. Install VS Code Extension
    Open a command or shell prompt to install extension
     ```
     $code --install-extension marus25.cortex-debug
     $code --install-extension Arm.environment-manager
     $code --install-extension Arm.cmsis-csolution
     ```
 3. Download cmsis-toolbox v2.0.0 and unzip it to D:\cmsis-toolbox
    https://github.com/Open-CMSIS-Pack/cmsis-toolbox/releases
 4. Install Himax.WE2_DFP.1.0.0.pack by using cmsis-toolbox cpackget
    Pack default location is ${HOME}/.cache/arm/packs for Linux and ${LOCALAPPDATA}/Arm/Packs for Windows
    Open a command or shell prompt
     ```
     $cd D:\cmsis-toolbox\bin
     $cpackget add https://www.keil.com/pack/ARM.CMSIS.5.9.0.pack
     $cpackget add https://www.keil.com/pack/ARM.CMSIS-FreeRTOS.10.5.1.pack
     $cpackget add https://www.keil.com/pack/ARM.CMSIS-NN.4.1.0.pack
     $cpackget add https://www.keil.com/pack/ARM.CMSIS-DSP.1.11.0.pack
     $cpackget add https://github.com/HimaxWiseEyePlus/cmsis-packs/raw/main/WE2_DFP/Himax.WE2_DFP.1.0.0.pack
     ```
 5. Copy /Arm/Packs/Himax/WE2_DFP/1.0.0/WE2_Ex/WLCSP65/CMSIS/ARM/hello_world_tz to D:\cmsis_test\hello_world_tz
    Remove read-only attribute from hello_world_tz folder
 6. VS Code menu bar select 'File -> Open Folder' open D:\cmsis_test\hello_world_tz
    In VS Code, right click vcpkg-configuration.json to show the pop-up menu 'Arm.environment-manager environment' and select activate environment
 7. VS Code menu bar select 'Terminal -> Run Task -> Build hello_world_tz ' to build hello_world_tz
     The two elf files, we2_cm55m_ns_app.elf and we2_cm55m_s_app.elf, will be generated.
 8. Download image_gen tool https://github.com/HimaxWiseEyePlus/cmsis-packs/raw/main/WE2_DFP/tool.7z
 9. Unzip tool to D:\cmsis_test\hello_world_tz
 10. VS Code menu bar select 'Terminal -> Run Task -> tool' to and select 'gen_image_mdk' to 
    merage elf files and WE2 bootloader.
    The complete image (output.img) will be generated in D:\cmsis_test\hello_world_tz\tool\we2_image_gen_local_exe_release_177231\output\
 11. VS Code menu bar select 'Terminal -> Run Task -> tool' to and select 'swd_progamming_flash' to 
    progam WE2 external NOR flash via SWD interface using pyOCD CMSIS-DAP.
 12. HW Reset WE2 board

# How to run debugging in VS Code ?
 - Requirement:
      - a. VS Code (v1.81.1 is tested)
      - b. VS Code Extension
         - marus25.cortex-debug (v1.6.10 is tested)
      - c. pyOCD_HX (see 'How to install pyOCD_HX ?')

 1. Modify vscode/launch.json for your system environment
      - svdFile
      - serverpath
 2. Modify vscode/settings.json for your system environment
   - cortex-debug.armToolchainPath.windows
   - cortex-debug.gdbPath.windows
   - cortex-debug.armToolchainPath.linux
   - cortex-debug.gdbPath.linux
 3. Select 'cortex-debug we2_cm55m_s_app Launch'VS Code in 'RUN AND DEBUG' Item.
 4. Press 'F5' to entery debug mode
    cortex-debug will be as gdb-client and pyocd will be local gdb-server.

# How to install pyOCD_HX ?
 - Requirement:
      - a. pyhon 3.x (v3.10.5 is tested)
      - b. python pip

 1. Download pyOCD_HX https://github.com/HimaxWiseEyePlus/cmsis-packs/raw/main/WE2_DFP/pyocd_hx-0.34.3.dev0+dirty-py3-none-any.whl
 2. Open a command or shell prompt to install
   ```
   $python -m pip uninstall pyocd
   $python -m pip uninstall pyocd_hx
   $python -m pip install pyocd_hx-0.34.3.dev0+dirty-py3-none-any.whl
   ```
 3. Check pyOCD_HX
   ```
   $pyocd --version (it should show 0.34.3.dev0+dirty)
   ```
# How to install pyOCD ?
 - Requirement:
      - a. pyhon 3.x (v3.10.5 is tested)
      - b. python pip

 1. Open a command or shell prompt to install
   ```
   $python3 -m pip uninstall pyocd
   $python3 -m pip uninstall pyocd_hx
   $python3 -m pip install pyocd
   ``` 
 2. Check pyOCD
    ```
    $pyocd --version (it should show 0.34.3 or higher version)
    ```
