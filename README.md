
# Slam Mirror Bot
This is a telegram bot writen in python for mirroring files on the internet to our beloved Google Drive.

<b> Modded Repo </b>

## Deploying on Heroku
Give Star & Fork this repo, then upload **token.pickle** & **credentials.json** to your forks

to know how to get them click on the  #[ link ](https://github.com/spe4641/test-new#getting-google-oauth-api-credential-file)

after this click on the below button 👇👇👇👇
<p><a href="https://heroku.com/deploy"> <img src="https://www.herokucdn.com/deploy/button.svg" alt="Deploy to Heroku" /></a></p>


## Features supported:

- Mirroring direct download links to Google Drive
- Create Tar Google Drive folder
- Mirroring Mega.nz links to Google Drive (In development stage)
- Mirroring Uptobox.com links to Google Drive (Uptobox account must be premium)
- Copy files from someone's drive to your drive (Using Autorclone)
- Download/upload progress, speeds and ETAs
- Docker support
- Uploading To Team Drives.
- Index Link support
- Service account support
- Heroku config support
- Extracting **tar.xz** support
- Mirror all youtube-dl supported links
- Stop duplicate cloning Google Drive & mirroring Mega support
- Limiting size Torrent/Direct, Mega, cloning Google Drive support
- Mirror telegram files
- Delete files from drive
- Add stickers to your pack
- Check Heroku dynos stats
- Nyaa.si and Sukebei Torrent search
- Shell and Executor
- Shortener support
- Custom Buttons
- Custom Filename (Only for url, telegram files and ytdl. Not for mega links and magnet/torrents)
- Speedtest with picture results
- Extracting password protected files and using custom filename see these examples:
- [Custom file name examples ](https://telegra.ph/Magneto-Python-Aria---Custom-Filename-Examples-01-20)
- Bot can extract the following types of files
```
ZIP, RAR, TAR, 7z, ISO, WIM, CAB, GZIP, BZIP2, 
APM, ARJ, CHM, CPIO, CramFS, DEB, DMG, FAT, 
HFS, LZH, LZMA, LZMA2, MBR, MSI, MSLZ, NSIS, 
NTFS, RPM, SquashFS, UDF, VHD, XAR, Z.
```

## Setting up config file
<details>
    <summary><b>Click here for more details</b></summary>

```
cp config_sample.env config.env
```
- Remove the first line saying:
```
_____REMOVE_THIS_LINE_____=True
```
Fill up rest of the fields. Meaning of each fields are discussed below:
### Required Field
- **BOT_TOKEN**: The Telegram bot token that you get from [@BotFather](https://t.me/BotFather)
- **TELEGRAM_API**: This is to authenticate to your Telegram account for downloading Telegram files. You can get this from https://my.telegram.org DO NOT put this in quotes.
- **TELEGRAM_HASH**: This is to authenticate to your Telegram account for downloading Telegram files. You can get this from https://my.telegram.org
- **OWNER_ID**: The Telegram user ID (not username) of the Owner of the bot
- **DATABASE_URL**: Your Database URL. See [Generate Database](https://github.com/breakdowns/slam-mirrorbot/tree/master#generate-database) to generate database. (**NOTE**: If you deploying on Heroku using Heroku button, no need to generate database manually, because it will automatic generate database when first deploying)
- **GDRIVE_FOLDER_ID**: This is the folder ID of the Google Drive Folder to which you want to upload all the mirrors.
- **DOWNLOAD_DIR**: The path to the local folder where the downloads should be downloaded to
- **DOWNLOAD_STATUS_UPDATE_INTERVAL**: A short interval of time in seconds after which the Mirror progress message is updated. (I recommend to keep it `5` seconds at least)  
- **AUTO_DELETE_MESSAGE_DURATION**: Interval of time (in seconds), after which the bot deletes it's message (and command message) which is expected to be viewed instantly. (**Note**: Set to `-1` to never automatically delete messages)
- **UPSTREAM_REPO**: Link for Bot Upstream Repo, if you want default update, fill ```https://github.com/breakdowns/slam-mirrorbot```.
- **UPSTREAM_BRANCH**: Branch name for Bot Upstream Repo (Recommended using master branch)
### Optional Field
- **AUTHORIZED_CHATS**: Fill user_id and chat_id of you want to authorize.
- **IS_TEAM_DRIVE**: Set to `True` if `GDRIVE_FOLDER_ID` is from a Team Drive else `False` or Leave it empty.
- **USE_SERVICE_ACCOUNTS**: (Leave empty if unsure) Whether to use Service Accounts or not. For this to work see [Using service accounts](https://github.com/breakdowns/slam-mirrorbot#generate-service-accounts-what-is-service-account) section below.
- **INDEX_URL**: Refer to https://github.com/ParveenBhadooOfficial/Google-Drive-Index The URL should not have any trailing '/'
- **MEGA_API_KEY**: Mega.nz api key to mirror mega.nz links. Get it from [Mega SDK Page](https://mega.nz/sdk)
- **MEGA_EMAIL_ID**: Your email id you used to sign up on mega.nz for using premium accounts (Leave th)
- **MEGA_PASSWORD**: Your password for your mega.nz account
- **BLOCK_MEGA_FOLDER**: If you want to remove mega.nz folder support, set it to `True`.
- **BLOCK_MEGA_LINKS**: If you want to remove mega.nz mirror support, set it to `True`.
- **STOP_DUPLICATE_MIRROR**: (Leave empty if unsure) if this field is set to `True`, bot will check file in Drive, if it is present in Drive, downloading will be stopped. (**Note**: File will be checked using filename, not using filehash, so this feature is not perfect yet)
- **STOP_DUPLICATE_MEGA**: (Leave empty if unsure) if this field is set to `True`, bot will check file in Drive, if it is present in Drive, downloading Mega will be stopped.
- **STOP_DUPLICATE_CLONE**: (Leave empty if unsure) if this field is set to `True`, bot will check file in Drive, if it is present in Drive, cloning will be stopped.
- **CLONE_LIMIT**: To limit cloning Google Drive (leave space between number and unit, Available units is (gb or GB, tb or TB).
- **MEGA_LIMIT**: To limit downloading Mega (leave space between number and unit, Available units is (gb or GB, tb or TB).
- **TORRENT_DIRECT_LIMIT**: To limit the Torrent/Direct mirror size, Leave space between number and unit. Available units is (gb or GB, tb or TB).
- **IMAGE_URL**: Show Image/Logo in /start message. Fill value of image your link image, use telegra.ph or any direct link image.
- **VIEW_LINK**: View Link button to open file Index Link in browser instead of direct download link, you can figure out if it's compatible with your Index code or not, open any video from you Index and check if the END of link from browser link bar is `?a=view`, if yes make it `True` it will work (Compatible with [Bhadoo Index](https://github.com/ParveenBhadooOfficial/Google-Drive-Index) Code)
- **UPTOBOX_TOKEN**: Uptobox token to mirror uptobox links. Get it from [Uptobox Premium Account](https://uptobox.com/my_account).
- **HEROKU_API_KEY**: (Only if you deploying on Heroku) Your Heroku API key, get it from https://dashboard.heroku.com/account.
- **HEROKU_APP_NAME**: (Only if you deploying on Heroku) Your Heroku app name.
- **IGNORE_PENDING_REQUESTS**: (Optional field) If you want the bot to ignore pending requests after it restarts, set this to `True`.
- **SHORTENER_API**: Fill your Shortener api key if you are using Shortener.
- **SHORTENER**: if you want to use Shortener in Gdrive and index link, fill Shortener url here. Examples:
```
exe.io, gplinks.in, shrinkme.io, urlshortx.com, shortzon.com
```

Above are the supported url Shorteners. Except these only some url Shorteners are supported.

**Note**: You can limit maximum concurrent downloads by changing the value of **MAX_CONCURRENT_DOWNLOADS** in aria.sh. By default, it's set to `7`.
### Add more buttons (Optional Field)
Three buttons are already added of Drive Link, Index Link, and View Link, you can add extra buttons, these are optional, if you don't know what are below entries, simply leave them, don't fill anything in them.
- **BUTTON_FOUR_NAME**:
- **BUTTON_FOUR_URL**:
- **BUTTON_FIVE_NAME**:
- **BUTTON_FIVE_URL**:
- **BUTTON_SIX_NAME**:
- **BUTTON_SIX_URL**:

</details>


## Getting Google OAuth API credential file

- Visit the [Google Cloud Console](https://console.developers.google.com/apis/credentials)
- Go to the OAuth Consent tab, fill it, and save.
- Go to the Credentials tab and click Create Credentials -> OAuth Client ID
- Choose Desktop and Create.
- Use the download button to download your credentials.
- clone this repo https://github.com/ayushteke/slam_aria_mirror_bot_HEROKU
- Move that file to the root of mirrorbot, and rename it to credentials.json
- install the requirements-cli.txt file by using

``` pip3 install -r requirements-cli.txt ```

- Visit [Google API page](https://console.developers.google.com/apis/library)
- Search for Drive and enable it if it is disabled
- Finally, run the script to generate **token.pickle** file for Google Drive:
```
python3 generate_drive_token.py
```

<b> Bot commands will be set automatically </b>
                 oR 

mirror - 🚀 /mirror DL or 🧲 self.

unzip - For Zipped file get unzip mirror.

tar - 🤐 upload.

cancel - cancel ID.

cnlall - cancel all.

list - list of mirror.

status - status.

auth - Permit a Chat [Owner only]

unauth - impermit a chat [Owner only] 

addsudo - Promote to sudo.[Owner only]

rmsudo - Depromote from sudo.[Owner only]

mediainfo - Get Detailed info about a media.

ping - speed test.

restart - restart bot [Owner Only]

stat - VSP status

hlp - help

log - Get logs [Owner only]

speedtest - speed of VPS

clone - clone G-File or Folder.

count - count files/folders on a 📂. 

watch - Mirror YTDL sites.

tarwatch - 🤐 mirror YTDL

del - Delete a file. 

usage - stats.

copy and paste this to <b> botfather </b>.


## Credits

Thanks to:
- Victim Soilder 
- [out386](https://github.com/out386) heavily inspired from telegram bot which is written in JS
- [Izzy12](https://github.com/lzzy12/) for original repo
- [Dank-del](https://github.com/Dank-del/) for base repo
- [magneto261290](https://github.com/magneto261290/) for some features
- [SVR666](https://github.com/SVR666/) for some fixes
- [4amparaboy](https://github.com/4amparaboy/) for some help
- [WinTenDev](https://github.com/WinTenDev/) for Uptobox support
- [iamLiquidX](https://github.com/iamLiquidX/) for Speedtest module
- [ydner](https://github.com/ydner/) for Usage module
- [breakdowns](https://github.com/breakdowns) for main repo
- [ayush](https://github.com/ayushteke) for nothing

