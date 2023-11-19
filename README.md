<a name="readme-top"></a>
<div align="center" id="Closebox73">
    <img src="https://github.com/closebox73/applying-theme/blob/main/Asset/Head.svg" width="450", height="300">
</div>

</br>

<p align="center">
  <img src="https://img.shields.io/github/stars/closebox73/applying-theme?style=for-the-badge&color=7DCFFF">
  <img src="https://img.shields.io/github/issues/closebox73/applying-theme?&style=for-the-badge&color=E0AF68">
  <img src="https://img.shields.io/github/forks/closebox73/applying-theme?&style=for-the-badge&color=F7768E">
  <img alt="GitHub last commit (by committer)" src="https://img.shields.io/github/last-commit/closebox73/applying-theme?style=for-the-badge&color=AD8EE6">
  <img src="https://img.shields.io/github/license/closebox73/applying-theme?style=for-the-badge&color=9ECE6A">
</p>

<p align="center">
This repository contains an explanation of how to use the conky theme that I made and what needs to be considered when using it, if something is unclear, please ask in the issue, Enjoy!!
</p>

## :writing_hand: Requirements :
### Main Applications :
- `Conky`<br />
  Version 1.10.8 or newer ( but i prefer to use 1.10.8 version ) open this  [Link](https://github.com/brndnmtthws/conky) for instalation from original source <br />
- `Lua`
- `Conky Manager`<br />
  If you want to use the GUI when installing the theme, please install [conky-manager2](https://github.com/zcot/conky-manager2)  
- `jq`<br />
  For the weather theme, the downloaded data is in the form of a json file, and jq is used to handle it, most distros already installed<br />
- `curl`<br />
  This command is used to download data from the web,it also most distros already installed<br />
  
### Music Player :
- `Mpd`<br />
  Because of my limited data plan, I prefer to listen to songs offline,LOL  
- `Playerctl`<br />
  For those who use online music players (such as spotify, youtube and others, even some offline ones can) In the future, I plan to use playerctl to get music player data that will be displayed in the theme, Instalation see [playerctl github](https://github.com/altdesktop/playerctl)

## :stop_sign: What to do before apply a theme :
- Syntax configuration of this theme for conky version 1.10.8 or newer
- The default folder for all theme that i made is in `~/.config/conky`<br />
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
  
	![](/Asset/Wlan.png)
  
  Number 3 is your device id,then overwrite the id in the config
- For theme that show weather information, you must have city_id that can you get from [Openweathermap](https://openweathermap.org) in the following way :
  - open the website then search your city :
  
	![](/Asset/owm1.png)
  
  - then select your city :
  
	![](/Asset/owm2.png)
  
  - copy the city_id :
  
	![](/Asset/owm3.png)
  - and then overwrite old city_id in weather-v2.0.sh which is in the scripts folder
- and for the api key, please use your own which you can get for free at openweathermap.org, in the following way:
  - Open the web and create an account
  - Verify your account first
  - Then at the homepage choose user option then choose My api key
  
	![](/Asset/api1.png)
  
  - Then copy your new api key 
  
	![](/Asset/api2.png)
  - Replace old apikey in in weather-v2.0.sh which is in the scripts folder
  - The api key that was just created can only be used a few hours after the account was created
  
- Install all font in fonts folder<br />
		- by open ttf file and click install<br />
		- or copy/move the ttf file to `~/.fonts`

	then update font cache by command :
  
  ```bash
  fc-cache -fv
  ```
  
  All fonts i get from:
	 - [Dafont](https://www.dafont.com)
	 - [Google Fonts](https://fonts.google.com)
	 
- For theme that showing battery status, if precentage is not appear.execute following command in terminal
  ```bash
  ls /sys/class/power_supply/
  ```
  Then overwrite default argument ( BAT0 ) with what was stated in the results of the execution of the command, the variable is `${battery_percent}`

- I currently use Openbox and XFCE, sometimes for other DE requires a slightly different setting<br />
  if you know how to set it on another DE (if an error occurs) please let me know and I will post it here<br />
	<details>
 	<summary><b>XFCE</b></summary>
	Even fellow XFCE users have different configurations, here's how to solve the error summarized by Yittri
	### Fixing transparency

  	1. First make sure compositing is enabled in xfwm. To do this open `Settings Manager > Window Manager Tweaks > Compositor >   Enable Display Compositing` should be checked.
  	2. In config file for the theme (for example for the Antares theme the config is in the root folder for that theme and called Antares.conf) change `own_window_argb_visual = false` to `own_window_argb_visual = true`

	### Making icons render

  	1. Move all the fonts in fonts file located in the theme folder to `~/.local/share/fonts`. If this folder does not exist, create it.
  	2. In a terminal run `fc-cache`

	### Making graphics appear

	I'm assuming the graphics don't work properly because the themes expect for conky to be compiled with cairo which is not available in the repositories by default.
	1.  In the aur download the PKGBUILD file for a package called conky-cairo. You can do this by running `yay -G conky-cairo` if you have yay installed. The file should be downloaded in a folder called conky-cairo.
	2. In the PKGBUILD file edit line 25 from `pkgver=1.11.3` to `pkgver=1.12.2` or whatever the latest version of conky is.
	3. If you're not using nvidia drivers change line 93 from `-D BUILD_NVIDIA=ON \` to `-D BUILD_NVIDIA=OFF \`.
	4. In the same folder as the PKGBUILD file run `makepkg -si`. 

	### Making conky start at login

	1. In `Setting Manager > Session and Startup > Application Autostart` click on the + button. 
	2. You can type anything in the name and description boxes but in the command box navigate to the `startup.sh` file for the theme.

	Not all points have to be done, just according to the error
	</details>
	
## :heavy_check_mark: How to use theme :
- After you download a theme,extract it then move theme folder to ~/.config/conky/
- Do the instruction above,then 
- There are 2 ways to activate the theme
  - Execute `start.sh`
  - If you use conky-manager2, just check the theme to be installed
  
	![](/Asset/CM2.png)
	- If theme in ~/.config/conky does not appear, do this
		- open Conky-manager and choose setting
		![](/Asset/cm01.png)
		
		- then choose location
		![](/Asset/cm02.png)
		
		- click add then navigate to ~/.config/conky then click open
		![](/Asset/cm03.png)
		
		- click OK then refresh conky-manager
		![](/Asset/cm04.png)
		
- Done

## :spiral_notepad: Frequent issues :
### :wrench: Transparent & faded image background in Gnome and KDE
  This issue often occurs in Gnome or KDE,one way to solve it is changing<br />  
	
  `own_window_argb_visual = false,` to `own_window_argb_visual = true,`
	
  Or the latest solution presentad by [Cristimc8](https://github.com/cristimc8) is by adding line below to the conky config
	
  `draw_blended = false,`
	
  Try experimenting with replacing it with true or false, if suddenly Conky doesn't appear don't panic, just undo and restart Conky  
  
### :wrench: Black background
  To solve this issue, you can experiment with theme transparency by using Conky-manager2, in the following way:
  - Open Conky-Manager2 then highlight the active theme
  
	![](/Asset/1trnsprnt.jpg)
  
  - Choose edit widget option
  
	![](/Asset/2trnsprnt.jpg)
  
  - Then Transparency
  
	![](/Asset/3trnsprnt.jpg)
  
  - Then Choose Pseudo-Transparent in Tranparency Type option
  
	![](/Asset/4trnsprnt.jpg)
  
  - Then Apply
  
	![](/Asset/5trnsprnt.jpg)
  
  - If still black, try other Transparency option.

### :wrench: Weather displays Null
  This Happened since there are limitations to API calls from openweather, I suggest creating your own api_key and then overwrite the one in weather-v2.0.sh or weather.sh to avoid error (appears Null )You can create it for free at [Openweathermap](https://openweathermap.org).

## :moneybag: Tip Jar :
if you like my themes, i will be very grateful if you are willing to make a donation to support me to make even better themes, thank you from all my heart. Using Paypal :

[![](https://img.shields.io/badge/PayPal-00457C?style=for-the-badge\&logo=paypal\&logoColor=white)](https://paypal.me/closebox73) 

or the easiest way is to download my theme on Pling Store :

[![](https://img.shields.io/badge/Pling_Store-FA5E0C?style=for-the-badge)](https://www.pling.com/u/closebox73x)

## :cyclone: Software used :
	- Conky *( Main Application )*
	- Gimp and Imagemagick *( To create a preview image )*
	- Inkscape *( to create a theme background )*
	- Geany or Neovim *( To edit config files and scripts )*
	- Alacritty *( to test the script or commands )*
	

<div align="center" id="Logo">
    <img src="https://github.com/closebox73/applying-theme/blob/main/Asset/Logo.svg" width="240", height="60">
</div>
</br>

<p align="center">
  <a href="https://t.me/closebox73x" target="_blank"><img alt="undefined" src="https://img.shields.io/badge/Telegram-D01DF0?style=for-the-badge&logo=telegram&logoColor=white"></a>
  <a href="https://twitter.com/closebox73" target="_blank"><img alt="undefined" src="https://img.shields.io/badge/Twitter-1D9BF0?style=for-the-badge&logo=twitter&logoColor=white"></a>
  <a href="https://discord.com/users/1115644269802311750" target="_blank"><img alt="undefined" src="https://img.shields.io/badge/Discord-%235865F2.svg?style=for-the-badge&logo=discord&logoColor=white"></a>
  <a href="https://matrix.to/#/@closebox73:matrix.org" target="_blank"><img alt="undefined" src="https://img.shields.io/badge/matrix-0A976F?style=for-the-badge&logo=Matrix&logoColor=white"></a>
</p>

<p align="center"><a href="#readme-top">---------- || Back to top || ----------</a></p>

<p align="center">
	<img src="https://api.visitorbadge.io/api/VisitorHit?user=closebox73&repo=applying-theme&countColor=%23FF00CC"
</p>

