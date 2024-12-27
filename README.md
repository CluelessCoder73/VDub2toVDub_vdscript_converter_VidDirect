# VDub2toVDub_vdscript_converter_VidDirect
This Python script is designed to convert a VirtualDub2 "vdscript" file into a format compatible with the original VirtualDub (.vdscript) application.

VirtualDub2 introduced certain changes and additional features to the .vdscript files, such as different video modes and additional commands. This script specifically modifies the following aspects to ensure compatibility with VirtualDub:

1. **Video Mode Conversion**:
   - The script replaces `VirtualDub.video.SetMode(3);` (used in VirtualDub2) with `VirtualDub.video.SetMode(0);` to set the video mode to "Direct Stream Copy" in VirtualDub.

2. **Command Removal**:
   - The script removes unnecessary lines that are present in VirtualDub2 scripts but are not required or may cause errors in VirtualDub. These include:
     - `VirtualDub.SaveFormatAVI();`
     - `VirtualDub.SaveAudioFormat("");`
     - `VirtualDub.video.filters.BeginUpdate();`
     - `VirtualDub.video.filters.EndUpdate();`

3. **Preservation of Edits**:
   - The script preserves all audio settings, video filter settings, and subset range selections made in VirtualDub2, ensuring that these edits are carried over seamlessly to VirtualDub.
This script was tested and works with:
- Python 3.12.5    
- VirtualDub2 (build 44282) .vdscript files
- VirtualDub 1.10.4   

Usage:
To use this script, simply call the `convert_vdscript()` function with the path to your VirtualDub2 script as the input and specify the desired output path for the converted VirtualDub script.

Example:
convert_vdscript("C:\\path\\to\\input_vdub2.vdscript", "C:\\path\\to\\output_vdub.vdscript")

This will generate a VirtualDub-compatible .vdscript file that can be opened and executed in the original VirtualDub application without errors.