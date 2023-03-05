# How to install my Conky theme collections

![](https://api.visitorbadge.io/api/VisitorHit?user=closebox73&repo=applying-theme&countColor=%231E90FF)

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
### Music Player
- `Mpd`<br />
  because of my limited data plan, I prefer to listen to songs offline,LOL 
- `Playerctl`<br />
  For those who use online music players (such as spotify, youtube and others, even some offline ones can)<br />
  In the future, I plan to use playerctl to get music player data that will be displayed in the theme
  
## :stop_sign: what to do before apply a theme :
- syntax configuration of this theme for conky version 1.10.8 or newer
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
  
  ![](/asset/owm3.png)
  and then overwrite old city_id in weather which is in the scripts folder
  
  
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
	 
- I currently use Openbox and XFCE, sometimes for other DE requires a slightly different setting<br />
  if you know how to set it on another DE (if an error occurs) please let me know and I will post it here<br />
	<details>
 	<summary><b>XFCE</b></summary>
	Even fellow XFCE users have different configurations, here's how to solve the error summarized by Yittri
	# Fixing transparency

  	1. First make sure compositing is enabled in xfwm. To do this open `Settings Manager > Window Manager Tweaks > Compositor >   Enable Display Compositing` should be checked.
  	2. In config file for the theme (for example for the Antares theme the config is in the root folder for that theme and called Antares.conf) change `own_window_argb_visual = false` to `own_window_argb_visual = true`

	# Making icons render

  	1. Move all the fonts in fonts file located in the theme folder to `~/.local/share/fonts`. If this folder does not exist, create it.
  	2. In a terminal run `fc-cache`

	# Making graphics appear

	I'm assuming the graphics don't work properly because the themes expect for conky to be compiled with cairo which is not available in the repositories by default.
	1.  In the aur download the PKGBUILD file for a package called conky-cairo. You can do this by running `yay -G conky-cairo` if you have yay installed. The file should be downloaded in a folder called conky-cairo.
	2. In the PKGBUILD file edit line 25 from `pkgver=1.11.3` to `pkgver=1.12.2` or whatever the latest version of conky is.
	3. If you're not using nvidia drivers change line 93 from `-D BUILD_NVIDIA=ON \` to `-D BUILD_NVIDIA=OFF \`.
	4. In the same folder as the PKGBUILD file run `makepkg -si`. 

	# Making conky start at login

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
  
	![](/asset/CM2.png)
	- If theme in ~/.config/conky does not appear, do this
		- open Conky-manager and choose setting
		![](/asset/cm01.png)
		
		- then choose location
		![](/asset/cm02.png)
		
		- click add then navigate to ~/.config/conky then click open
		![](/asset/cm03.png)
		
		- click OK then refresh conky-manager
		![](/asset/cm04.png)
		
- Done

## :cyclone: Software used :
	- Conky
	- Gimp
	- Inkscape
	- Geany
	- Alacritty

## :moneybag: Tip Jar :
if you like my themes, i will be very grateful if you are willing to make a donation to support me to make even better themes<br />
thank you from all my heart

[![](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/closebox73)

[![Support via PayPal](https://cdn.rawgit.com/twolfson/paypal-github-button/1.0.0/dist/button.svg)](https://www.paypal.me/closebox73/)

or the easiest way is to download my theme on [Pling.com](https://www.pling.com/u/closebox73x) 

![greetings](/Asset/logos.png)
