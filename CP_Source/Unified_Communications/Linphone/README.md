# Linphone VoIP/SIP Client

|  CP Information |            |
|--------------------|------------|
| Package | Linphone - Current Version |
| Script Name | none |
| CP Mount Path | /custom/linphone |
| CP Size | 300M |
| IGEL OS Version (min) | 11.3.110 |
| Metadata File <br /> linphone.inf | [INFO] <br /> [PART] <br /> file="linphone.tar.bz2" <br /> version="filled in from script" <br /> size="300M" <br /> name="filled in from script" <br /> minfw="11.03.110" |
| Path to Executable | /custom/linphone/AppRun |
| Path to Icon | /custom/linphone/linphone.svg|
| Missing Libraries | none |
| Download package and missing library | none |
| Packaging Notes | The CP Linphone is build from an AppImage. There will run on Linux without installation,  because everthing they need is build into that package. AppImages are like .ISO files and not changeable.<br /> So why does this script extract the AppImage into a CP?<br /> This AppImage checks for a newer version and then offers the user to download this update as an AppImage. But this is not possible on IGEL OS. To disable this, one line in a file has to be changed (usr/share/linphone/linphonerc-factory, see build script).<br /> <br /> The reason to move the initialisation of persistency to the profile (Desktop Final) instead of custompart-linphone:<br /> Linphone uses ~/.config/linphone and  ~/.local/linphone/ to store data. I found out linking these directories at CP creation time interferes with systemd. So I need to establish this functionality later in the boot process. Custom Commands -> Desktop Final will call [desktop-final.sh] to link the needed directories.|
|Package automation | [build-linphone.sh](build-linphone.sh) <br /><br /> Tested with FW11.03.500, FW11.04.240 |