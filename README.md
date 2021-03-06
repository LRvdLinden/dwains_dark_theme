<h1 align="center">Dwains Dark Theme</h1> 


<p align="center">
  <a href="https://github.com/LRvdLinden/dwains_dark_theme">
    <img src="https://img.shields.io/github/v/release/LRvdLinden/dwains_dark_theme" />
  </a>
    <a href="https://github.com/LRvdLinden/dwains_dark_theme/commits">
    <img src="https://img.shields.io/github/last-commit/LRvdLinden/dwains_dark_theme.svg?style=plasticr" />
  </a>
    <a href="https://github.com/LRvdLinden/">
    <img src="https://img.shields.io/github/followers/LRvdLinden?style=social" />
  </a>
    </a>
    <a href="https://discord.gg/7yt64uX">
    <img src="https://img.shields.io/discord/688401603811999885" />
  </a>
</p>

<p align="center">A Lovelace Dark theme based on <a href=https://github.com/dwainscheeren/dwains-lovelace-dashboard>Dwains Dashboard</a></p>
<p align="center">Created by <a href="https://github.com/LRvdLinden">Léon van der Linden</a></p> 

<p align="center">
  <img src="https://user-images.githubusercontent.com/77990847/114923935-b312c200-9e2d-11eb-81b2-3ae17998b3dd.png" />
</p>

<p align="center">Also take a look at <a href="https://github.com/LRvdLinden/dwains_light_theme">Dwains Light Theme</a></p> 

| **Dwains Light Theme** | **Dwains Dark Theme** | 
| ----------- | ----------  | 
| ![Dwains Light Theme](https://user-images.githubusercontent.com/77990847/118010920-bf683d00-b34f-11eb-8f6d-776989c05a2f.png) | ![Dwains Dark Theme](https://user-images.githubusercontent.com/77990847/118010912-becfa680-b34f-11eb-88ec-f2b5d6be2e5a.png) | 

## Prerequisite ⚙️
---
- Make sure you can access youre Home Assistant config files with [Samba Share](https://www.youtube.com/watch?v=udqY2CYzYGk) or [ssh](https://community.home-assistant.io/t/home-assistant-community-add-on-ssh-web-terminal/33820)


## Installation Dwains Dark Theme ⚙️
---
- Download the `themes` folder and place `dwains_dark_theme` in to your `config/theme` directory.
- Make shure you have created a `themes` folder in youre `config/` directory and added the following code to youre `configuration.yaml`
```yaml
# Core Configuration
default_config:
frontend:
  themes: !include_dir_merge_named themes/
```
- Reboot Home Assistant or after installation Dwains Dark Theme

## Selecting Dwains Dark Theme 🔧
---
- Click on youre profile picture
- By `themes` you need to select Dwains Dark Theme 

![image](https://user-images.githubusercontent.com/77990847/114926311-7bf1e000-9e30-11eb-8193-d669545a642d.png)

## Automation options 🔧
---
### Set HA theme for day and night
- When you want to switch automatic between the Dark and Light theme based on the sun, please copy the file `auto_switch_theme.yaml` into youre `automations.yaml` or `directory`
- Reboot Home Assistant
```yaml
- alias: Set HA theme for day and night
  id: set_theme_for_day_and_night
  trigger:
    - platform: homeassistant
      event: start
    - platform: state
      entity_id: sun.sun
      to: above_horizon
    - platform: state
      entity_id: sun.sun
      to: below_horizon
  action:
    - service: frontend.set_theme
      data:
        name: >
          {% if states.sun.sun.state == "above_horizon" %}
            Dwains Light Theme
          {% else %}
            Dwains Dark Theme
          {% endif %}
```
### Automation for default theme after starup HA
- When you want to have a default theme after startup HA, please copy the file `set_theme_at_startup.yaml` into youre `automations.yaml` or `directory`
- Reboot Home Assistant
```yaml
- alias: 'Set theme at startup'
  trigger:
    platform: homeassistant
    event: start
  action:
    service: frontend.set_theme
    data:
      name: Dwains Dark Theme
```

## State icons 🎨
---
| Name | Type | Default | Since | Code |
|------|:--------------:|:-------:|:-----:|:--------------:|
| state icon | color | ![ ](https://dummyimage.com/20x10/299ec2&amp;text=+) `#299ec2` | v2.0.1 | color: var(-- state-icon-active-color) |
| active icon  | color | ![ ](https://dummyimage.com/20x10/ffd60a&amp;text=+) `#ffd60a` | v2.0.1 | color: var(--state-icon-color) |
| unavailable icon | color | ![ ](https://dummyimage.com/20x10/a9b1bc&amp;text=+) `#a9b1bc` | v2.0.1 | color: var(--state-icon-unavailable-color) |

## Fonts 🎨
---
### Theme font (HA)
- If you whant to change the font of HA, you can change the [Google font](https://fonts.google.com/) in theme theme file on line `8`
```yaml
primary-font-family: 'Open Sans' # <- if you whant to change the font, fill in de richt google font name between ''
```

### Dwains Dashboard font
- If you want to change the fonnt from Dwains Dashboard, to get it the same as your HA theme, go to the dashboard theme files in directory `/config/custom_components/dwains_dashboard/lovelace/themefiles/`
- Open the dashboard theme `.yaml` file
- Search for `primary-font-family: 'Open Sans'`
- Fill in the right [Google font](https://fonts.google.com/) name between `''`
- Reboot Home Assistant

## Dark and Light Theme 🎨
---

| Icon | Place | Type |
|------|:-------:|:--------------:|
| 🎨 | Lovelace Theme | [Dwains Light Theme](https://github.com/LRvdLinden/dwains_light_theme) | 
| 🎨 | Lovelace Theme | [Dwains Dark Theme](https://github.com/LRvdLinden/dwains_dark_theme) | 

| **Dwains Light Theme** | **Dwains Dark Theme** | 
| ----------- | ----------  | 
| ![Dwains Light Theme](https://user-images.githubusercontent.com/77990847/118010920-bf683d00-b34f-11eb-8f6d-776989c05a2f.png) | ![Dwains Dark Theme](https://user-images.githubusercontent.com/77990847/118010912-becfa680-b34f-11eb-88ec-f2b5d6be2e5a.png) | 

## Result
---
![image](https://user-images.githubusercontent.com/77990847/114926388-91670a00-9e30-11eb-8747-570b62393dc8.png)
![image](https://user-images.githubusercontent.com/77990847/114923935-b312c200-9e2d-11eb-81b2-3ae17998b3dd.png)
---
Enjoy my Lovelace theme? Help me out for a couple of :beers: or a :coffee:!

[![coffee](https://www.buymeacoffee.com/assets/img/custom_images/black_img.png)](https://www.buymeacoffee.com/LRvdLinden)
