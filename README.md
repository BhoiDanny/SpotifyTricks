# SpotifyTricks

# Spotify Tricks

This is a collections of script, patches and procedures to mod Mobile and Desktop Spotify Applications<br>
If you know about something that isn't listed here and you would like it to be feel free to tell me about it in the comments or send an e-mail to dav@davoleo.net


## Disabling Ads

#### Desktop (Windows)

Install the new fork of **[BlockTheSpot](https://github.com/mrpond/BlockTheSpot)**


*Note: If you have the Windows Store version of Spotify or you don't feel very confident use the "Semi-Automatic installation" method that installs the right version of Spotify and BlockTheSpot for you.*

##### Semi-Automatic installation:
- Download/Make a copy of [this script file](https://github.com/mrpond/BlockTheSpot/blob/master/BlockTheSpot.bat) on your computer and double click it<br>
or
- Run this command in Powershell: 
```powershell
Invoke-WebRequest -UseBasicParsing 'https://raw.githubusercontent.com/mrpond/BlockTheSpot/master/install.ps1' | Invoke-Expression
```

##### Manual Installation
- Browse to this page: https://github.com/mrpond/BlockTheSpot/releases
- Download the `chrome_elf.zip` package of the latest available version
- Press `Start + R` and write `%appdata%` and then press `Enter` (this will get us into the Roaming Appdata Directory of our computer)
- Look for a directory called `Spotify`, double click it
- Extract the contents of the downloaded package (both `chrome_elf.dll` and `config.ini`) directly into the Spotify Folder
- Click yes, when asked to replace the original files with the patched ones

##### Important Notes
The semi-automatic script will download the latest copy of the patch and apply it to Spotify.
You should keep the script file on your computer somewhere so you don't have to download it every time you need to patch the Spotify again.
You may need to patch it again whenever there's a new update for Spotify and the patch gets overridden
*Important Note: After updating and Changing Theme via spicetify Spotify will need to be patched again by BlockTheSpot for it to work properly*

#### Mobile (Android)

##### Steps
- Uninstall any previous version of Spotify you may have had before
- Allow non-PlayStore apps installation in the settings
- Download and Install [xManager-v2 for spotify](https://github.com/xManager-v2/xManager-Spotify/releases/latest)
- Once opened this app will allow to install and update modded spotify versions as soon as they're out (you can also install an AMOLED Themed version, if you're display supports AMOLED)



## Theming the Desktop App

To inject a custom theme into spotify we'll use a command line utility called Spicetify

#### Spicetify CLI

*Note: if you want to install this on a different OS than Windows please refer to the [spicetify CLI wiki](https://github.com/khanhas/spicetify-cli/wiki/Installation)*

##### Install Instruction (Windows):
- Press `Start + R`, then write `powershell` and press `Enter` in the window that shows up
- In the powershell window that opens run this command: 
```powershell 
Invoke-WebRequest -UseBasicParsing "https://raw.githubusercontent.com/khanhas/spicetify-cli/master/install.ps1" | Invoke-Expression
```
- If any issue with downloading occurs run this command instead:
```powershell
Invoke-WebRequest -UseBasicParsing "https://raw.githubusercontent.com/khanhas/spicetify-cli/master/install_curl.ps1" | Invoke-Expression
```
- Open a command Prompt and run `spicetify` to generate default configuration files
- Download the theme you like the most from [this repository](https://github.com/morpheusthewhite/spicetify-themes) (see the note below)
- Find out the path of the config file by running `spicetify -c`
- Open the ini file with a text editor and change the `current_theme` entry to the name of the folder of the Theme you've downloaded
- Then open the folder the `config.ini` file is stored into, and then go into the `Themes` subdirectory
- Move the folder of the Theme you've chosen inside the Themes folder
- Then run `spicetify backup apply` or `spicetify apply` depending if a spotify update was just installed

*Note: To download themes from the community repository you need to download the repo sources as a zip or cloning the repository with git and then take the folder of the theme you want to apply and copy it*




## Downgrading the Desktop App

There might be some reasons you might want to downgrade Spotify to a certain version 
(for example, recently `June/July 2021` spicetify is broken on the latest Spotify Version and the only way to fix is to downgrade Spotify to the latest compatible version)<br>
(or to restore the old UI before the Spotify updates of `April/June 2021`)<br>

Here I'll be explaining how you can downgrade Spotify as well as making it a permanent downgrade that you can disable whenever you want manually.

### Downgrading and Blocking updates

1. Document yourself on the version you're interested in having installed, then download it from this [repository](https://spotify.en.uptodown.com/windows/versions)
2. Uninstall any Spotify version you already had on your machine (and cleanup any remeaining Spotify files/folders in `%appdata%` and `%localappdata%` directories)
3. Install the old version you downloaded from the repository above. (_Don't log into your account after having installed the old version_)
4. Open `%appdata%\Spotify` again and here create a new file changing it's name to `Spotify_new.exe` (be sure to change the actual extension and not to save it as a normal text file [if you don't see extension in the Explorer you can go in View section above and tick `File Name Extensions`])
5. Right click on that file -> Properties and tick the `Read-Only` checkbox
6. Open `%localappdata%\Spotify` here create a new folder called `Update` and be sure that it's empty then right click it go into `Properties` and then into the `Security` Tab
7. In the security tab you need to click `Edit...` and then check `Deny` on `Full Control` for each group/user name in the list above, then press Apply (as a proof you did correctly you should get a permission error when you try to open the folder)
8. After this you've successfully blocked Spotify Updates

### Unblocking Spotify Updates 

1. Open `%localappdata%\Spotify` and open the properties of the `Update` folder
2. Now in the `Security` tab you need to remove all the permission denial you added to block updates
3. To do that click on `Edit...` and for each group/user name you need to uncheck the `Deny` checkbox for all permissions in the list.
4. After that just keep using Spotify as normal and eventually the update to the latest version should pop up.



## Bypass Country Restrictions

It is known that some songs on Spotify are released and available for a limited number of countries usually due to labels and artists restricting the license under which they release songs.

If you happen to see songs that are greyed out like this:
![country_restrictions](https://i.imgur.com/Dvftro4.png)
Then you could try using a tool like https://kira.vercel.app to find out where these songs are available

If you're looking through a playlist you might not see unavailable songs at all if you have this option disabled in your Spotify Settings, so make sure that's enabled
![playlist_hidden_tracks](https://i.imgur.com/OP9ofHQ.png)

You can bypass country restrictions with a Free VPN (even the ones that have a low free quota work just fine) and a Free Spotify Subscription

##### Steps:
1. Access to a country you know the song is available in via the VPN Service
2. Login on spotify.com 
3. Click Profile at the top right and then Account
4. Click Profile and change your 'Country' to the one you want (you should see the option if you're accessing the website correctly through the VPN)
5. Then you can shutdown the VPN as you won't need it anymore
6. After changing the country there you should be able to listen to any song available in that country for about 14~15 days
7. After the timespan has passed you need to change the Country back to your original country and start again from step **1.** if you want to listen to those blocked songs again

##### What do I do if I have a Premium subscription?
You can't apply the same steps listed above if you have (or you've had in the past) a Premium subscription to Spotify because spotify stores your country information from the credit card you've used to pay the subscription, the only way (that I know of) to change your country with a premium subscription is to get someone else from another country to use their credit card to pay your subscription or to pay a new subscription with a card that has different country information.

##### Additional Notes:
§ There are some countries that have an additional listening limit:<br>
Japan:
- Premium Subscribers are not affected
- 15 hours limit
- Resets once every 30 days beginning with the login
- This affects every kind of device except mobiles (patched android mobile application count as tablets)

_While there's only one country that has restriction that I know of there may be others, feel free to tell me about others in the comments if you know them_




## Saving Spotify Songs Locally

Disclaimer: While there is NO way currently to download spotify songs directly from their API with a Free Subscription or with any hacky method there are solution that allow you to achieve similar things, I'm here to write about 2 of those I know

### Spytify

Spytify is a way to get Spotify streamed songs locally on your device, it works by recording Spotify's streamed sound.

##### Pros: 
- You can get any song you can stream on Spotify locally without a Premium Subscription
- Works really well with the Country-Restriction-Bypass I wrote about before to stream and record region-blocked songs
##### Cons:
- It's not a download so you have to stream the song at least once before being able to listen to it locally
- It's _Windows-Only_
- You can only record songs up to 320kbps (Spotify Premium) or up to 160kbps (Spotify Free) of bitrate quality (lossy MP3)

##### Steps:
- Download Spytify from https://jwallet.github.io/spy-spotify/overview.html
- Read about the tool on the different pages of the website linked above
- Extract the zip file on your computer
- Setup Spytify to your needs
- Start a session to record your Spotify Songs

### Deemix

Allows you to download songs from Deezer Music.<br>

##### Pros: 
- You can download songs of any quality from lossy mp3 to lossless flac
- You can input directly the spotify song link
##### Cons: 
- Not all songs that are released on spotify are also released on Deezer Music

##### Steps:
- Download the latest deemix-pyweb version [here](https://download.deemix.app/0:/pyweb/) and extract/install it
- Open the settings, in the Login section click "How do I get my own ARL?" and follow the guide to get your ARL
- Paste your ARL inside the right text box and save
- Once you're logged in scroll to the end of the settings to find the Spotify Features section
- Click on the link "How do I enable Spotify Features?" and follow the guide
- Paste all the information in the right text boxes and save

Note: By default deemix will download songs in MP3 format at 320kbps of bitrate although you can change it in the Downloads section of the settings

Now you're all set and you can paste links to spotify songs to download them together with all their metadata / Otherwise you can just look for a song in Deezer and download it
