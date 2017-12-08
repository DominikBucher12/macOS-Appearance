# macOS-Appearance

reference: [AQUA-LICK](https://github.com/ExactProbability/AQUA-LICK-GIT)
# What is this?
This repository has been made for the sake of anyone wanting to customize their macOS theme to the max. 

# Why the f*** would you do that?
If you are NERD who needs customize everything and come up with new awesome colors to your interface, now its your time - you will like this idea and proof of concept that we can add MORE than just Graphite and blue Appearance to the Aqua interface. Of course it involves a bit of effort to color up something. But hey, that's what life is, not? 

# Where to start?

##### First of all you will need:
1. [imageMagick](https://www.imagemagick.org/script/download.php)
2. [ThemeEngine](https://github.com/alexzielenski/ThemeEngine)
3. Brain
4. Read this readme carefully.
5. Not be afraid of asking/experimenting
6. Maybe turn of `SIP` (I hope not)

You can start with creating your custom theme from the scratch, fork this repo, take the png images exported from the *.car files and start painting/designing (You can use or update my scripts in this repo). After you are done with the job, you can either contribute to my repo or keep it to yourself. I have not found a way yet to add more options of Appearance into the settings, but I was hacking a bit around and I think it won't be easy task because the keys for those are hardcoded etc. So the hotfix for this is to replace the Graphite appearance for your own. For now, when I make more inspections, I will take a look if this is even possible.

~~Only thing you need to do is to add the assets to xcasset and then compile it to *car file via `xcrun actool` command. If you are not familiar with this - open issue and I will try to help you. Before opening issues please check out the docs for this:
https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/actool.1.html 
which sure doesnt't tell much. So feel free after reading this to report issue...~~

Please leave `xcrun actool` out of this for sake of your nerves. But if you are curious how to actually make archive `.xcasset` files, first get the right manual:
`nroff -man /Applications/Xcode.app/Contents/Developer/usr/share/man/man1/actool.1 | less`

then use this:
`xcrun actool --compile build --platform macosx --minimum-deployment-target 10.13 /path/to/Any.xcassets /path/to/Exported.car`

# Steps to happiness

For now I developed some kind of workflow, which sucks and to be flawlessly working requires updating the ThemeEngine app, which is sure awesome. 

1. Create your copy of `Vanilla` Folder from this repo and name it as you like for instance `Custom Appearance`
2. Open up terminal and change directory to `GraphiteDarkAppearance` in your `Custom Appearance` folder.
3. To ease your pain, the color of gray is +- `rgb(142,142,147)` which is `#8e8e93` in hex... To explain why we need this: Simply we want to replace the gray color with ours, so we use `mogrify` command (keep in mind you have to be at the directory):
```mogrify -format png -fuzz 30% -fill "#e273df" -opaque "#8e8e93" *.png```
4. viola we have colored whole folder of assets
5. Now we open up `ThemeEngine` and open our `GraphiteDarkAppearance.car` file, because of limitations, quite a drag that we have to replace those files one by one, but if you'd like, you can contribute with me and make the program more awesome than it already is.
6. When done replacing the assets in the compiled file replace the file located in `/System/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/` 
7. Repeat for another (light) design. If you replace only Dark Appearance, only Applications with dark mode will have those new attributes: `Source tree` is great example:

# Steps to contribute
1. Checkout or Fork this repo
2. Make new Folder with name which best describes your new theme
3. Design the assets according to your desires. (imageMagick should help you)
4. When done, you can just submit a pull request to my repo or keep it on your own
5. Ping me or help me for script which will replace the current Appearance
 
# Proof of concept: 

##### Given 
the assets located at this path `/System/Library/CoreServices/SystemAppearance.bundle/Contents/Resources/`, 
with some effort and research I was able to change the Graphite default Keyboard-active Textfield margin color + The Color of window buttons in dark mode (Will change in light too)
Video [here](https://instagram.com/p/Bbm8WP5BU9y/) and yes, I share my IG video...

##### When
a) Using this awesome tool:  https://github.com/alexzielenski/ThemeEngine I got to inspect the png files and extract them, change them with imageMagick and then 

b) With the other one: https://github.com/insidegui/AssetCatalogTinkerer I got to export the PNG files to change. (To be continued with this way, seems like it's compiling those files somehow not the way it needs to be...)

##### Then 
all you need to do after disassembling and changing the car files is to put them back together. `actool` from Xcode utilities does this incredible thing. And it's just the cost of figuring the heck outta thing because the documentation is really poor.

Because I couldn't figure out some steps, they might seem odd or unreasonable, so you can correct me when I'm wrong... Feel free to open up issue, contact me, blame me and so on...





