<a name="readme-top"></a>
<div align="center" id="Draco">
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
<p><strong>Main Applications</strong></p>
- `Conky`<br />
  Version 1.10.8 or newer ( but i prefer to use 1.10.8 version ) open this  [Link](https://github.com/brndnmtthws/conky) for instalation from original source <br />
- `Lua`
- `Conky Manager`<br />
  If you want to use the GUI when installing the theme, please install [conky-manager2](https://github.com/zcot/conky-manager2)  
- `jq`<br />
  For the weather theme, the downloaded data is in the form of a json file, and jq is used to handle it, most distros already installed<br />
- `curl`<br />
  This command is used to download data from the web,it also most distros already installed<br />
<p><strong>Music Player</strong></p>
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
	 
- For theme that showing battery status, if precentage is not appear.try to search and change variable `${battery_percent}` with `${battery_percent BAT1}` ( or other number )
	 
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
	
	<details>
 	<summary><b>GNOME</b></summary>
	as far as I know, the error in Gnome is only about transparency, and this can be solved by changing<br />
	`own_window_argb_visual = false` to `own_window_argb_visual = true`
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

## :cyclone: Software used :
	- Conky
	- Gimp
	- Inkscape
	- Geany
	- Alacritty

## :moneybag: Tip Jar :
if you like my themes, i will be very grateful if you are willing to make a donation to support me to make even better themes, thank you from all my heart

[![Support via PayPal](https://cdn.rawgit.com/twolfson/paypal-github-button/1.0.0/dist/button.svg)](https://www.paypal.me/closebox73/)

or the easiest way is to download my theme on [Pling.com](https://www.pling.com/u/closebox73x)

![](https://api.visitorbadge.io/api/VisitorHit?user=closebox73&repo=applying-theme&countColor=%231E90FF) 

![](/Asset/logos.png)
<p align="center"><a href="#readme-top">---------- || Back to top || ----------</a></p>
