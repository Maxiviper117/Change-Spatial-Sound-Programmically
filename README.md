# WIP - NOT COMPLETE

# Change-Spatial-Sound-Programmically

Adjusting spatial sound settings such as Windows Sonic or Dobly Atmos in Windows 11 can be a time-consuming and cumbersome task. Users are required to navigate through multiple menus to toggle settings to a different option or turn them off completely. As a user of Corsair HS65 headphones with Dolby Atmos support, I often find myself needing to toggle spatial sound off depending on the game or video I'm watching. However, there are no readily available shortcut keys to simplify the process, making it unnecessarily complicated.

# Windows

## Download `SoundVolumeView` 
- from: https://www.nirsoft.net/utils/sound_volume_view.html
## Extract ZIP 
- Extract to folder somewhere on your PC like `C:\SoundVolumeView`
- SoundVolumeView program allows `"extensive command-line support, which allows you to save/load profiles, change current volume of every sound component, and mute/unmute every sound component, without displaying any user interface."`

## Add this folder Path to Environment Variables
We need to add the `SoundVolumeView.exe` to PATH to enable use to execute a script from anywhere, shown later in the steps.

1. Press `Win + X`
2. Click on **System**
3. Click on **Advanced system settings**
	- Or search in start menu: 
	- ![image](https://user-images.githubusercontent.com/11472492/228288232-22fa5257-2cdb-4c54-89f4-e017a13f4b98.png)
4. Go to the **Advanced** tab
5. Click on the **Environment Variables** button
6. Locate **Path** under **System variables**
   - If **Path** exists, select and click on **Edit**
   - If **Path** doesn't exist, click on **New**
7. If you clicked **Edit** in step 6:
   - Click on the **New** button
   - Enter `C:\SoundVolumeView`
   c. Click on **OK**
8. If you clicked **New** in step 6:
   - Enter **Path** as the variable name
   - Enter `C:\SoundVolumeView` as the variable value
   - Click on **OK**
9. Click on **OK** to close Environment Variables window
10. Click on **OK** to close System Properties window
11. Restart any open command prompt or PowerShell windows

## Get Device Name of Headphones
- Open `SoundVolumeView` directly
- Take note of Device Name
	- Example from my system: `CORSAIR HS65 SURROUND USB Adapter`
	- ![image](https://user-images.githubusercontent.com/11472492/228289670-06558592-122e-4a2d-a58d-ceb73f0bef50.png)


## Python
- Install auto-py-to-exe `pip install auto-py-to-exe`
- This will allow us to convert the `.py` file to a `.exe` file

Commands
```powershell
SoundVolumeView.exe /SetSpatial "CORSAIR HS65 SURROUND USB Adapter" "Windows Sonic For Headphones"
SoundVolumeView.exe /SetSpatial "CORSAIR HS65 SURROUND USB Adapter" "Dolby Atmos For Headphones"
SoundVolumeView.exe /SetSpatial "CORSAIR HS65 SURROUND USB Adapter" "Off"
```

### Python Scripts
#### Create python file such as: `SetSpatialSound_Off.py`
#### Paste Script Below But Change Device Name  `"CORSAIR HS65 SURROUND USB Adapter"` to your own Device Name Retrieved from SoundVolumeView Program
```python
import subprocess

command = [
    "powershell.exe",
    'SoundVolumeView.exe /SetSpatial "CORSAIR HS65 SURROUND USB Adapter" ""'
]

subprocess.run(command, shell=False, text=True, capture_output=True)

```
#### Create python file such as: `SetSpatialSound_Dolby_Atmos.py`
#### Paste Script Below But Change Device Name  `"CORSAIR HS65 SURROUND USB Adapter"` to your own Device Name Retrieved from SoundVolumeView Program
```python
import subprocess

command = [
    "powershell.exe",
    'SoundVolumeView.exe /SetSpatial "CORSAIR HS65 SURROUND USB Adapter" ""'
]

subprocess.run(command, shell=False, text=True, capture_output=True)

```
#### Create python file such as: `SetSpatialSound_Windows_Sonic.py`
#### Paste Script Below But Change Device Name  `"CORSAIR HS65 SURROUND USB Adapter"` to your own Device Name Retrieved from SoundVolumeView Program
```python
import subprocess

command = [
    "powershell.exe",
    'SoundVolumeView.exe /SetSpatial "CORSAIR HS65 SURROUND USB Adapter" ""'
]

subprocess.run(command, shell=False, text=True, capture_output=True)

```
