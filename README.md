# How to install my Conky theme collections

## :writing_hand: Requirements :
- `Conky`<br />
  version 1.10.8 or newer ( but i prefer to use 1.10.8 version )<br />
  open this  [Link](https://github.com/brndnmtthws/conky) for instalation from original source <br />
- `Lua`
- `jq`<br />
  for the weather theme, the downloaded data is in the form of a json file, and jq is used to handle it<br />
  most distros already installed<br />
- `curl`<br />
  This command is used to download data from the web,it also most distros already installed<br />
- `Conky Manager`<br />
  if you want to use the GUI when installing the theme, please install [conky-manager2](https://github.com/zcot/conky-manager2)
  
## :stop_sign: what to do before apply a theme :
- syntax configuration of this theme for conky version 1.10.8 or newer  ( but i prefer to use 1.10.8 version )
- the default folder for all theme that i made is in `~/.config/conky`<br />
  if it doesn't exist please create one, some people use ~/.conky/ or maybe use their $home<br />
  if you do it can cause the theme to be broke,because everything is linked
- The music player I used was `mpd`, if you use other music player the status is will not appear<br />
  but you can edit the config to match what you want
- For theme that show network status ( speed, graph or usage ), you must know your device id,
  to check it run this command
  
  ```bash
  ip link
  ```
  then it will appear like this
  
	![](/asset/Wlan.png)
  
  Number 3 is your device id,then overwrite the id in the config
- For theme that show weather information, you must have city_id that can you get from [Openweathermap](https://openweathermap.org) in the following way :
  open the website then search your city :
  
  ![](/asset/owm1.png)
  
  then select your city :
  
  ![](/asset/owm2.png)
  
  copy the city_id :
  
  ![](/asset/owm2.png)
  
- Install all font in fonts folder, then update font cache by command :
  
  ```bash
  fc-cache -fv
  ```
- I currently use Openbox and XFCE, sometimes for other DE requires a slightly different setting
	if you know how to set it on another DE (if an error occurs) please let me know and I will post it here 

## :heavy_check_mark: How to use theme :
- Make sure theme folder is in ~/.config/conky/
- There are 2 ways to activate the theme
  - Execute `start.sh`
  - If you use conky-manager2, just check the theme to be installed
	![](/asset/CM2.png)
- Done
