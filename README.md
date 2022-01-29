This is a Telegram Bot written in Python for mirroring files on the Internet to your Google Drive or Telegram. Based on [python-aria-mirror-bot](https://github.com/lzzy12/python-aria-mirror-bot)
### Fork of Anasty's Repo previously know as Slam Mirror Repo

# Features:
<details>
    <summary><b>Click Here For More Details</b></summary>
## By me
- Defining Commands in config.env
- Defining Telegraph Ui elements in config.env
- Log Chat support for mirror
- Leech log for leech
- Force subscriber module
- Heroku Dyno Usage module

</details>

# How to deploy?
## Simplest and easiest way
```
- Fork this repo
- Download the sample_config.env file
- Change it's name to config.env
- Remove the first line saying" _____REMOVE_THIS_LINE_____=True
- Fill all the config vars
- Create another private repo on github upload your config file there and get the "RAW URL" of that file
- Go to your forked repo setting and in secrates fill the values of
- HEROKU_API_KEY - "Your Heroku API"
- HEROKU_EMAIL - "Your Heroku Email"
- HEROKU_APP_NAME - "Your Heroku App name"
- CONFIG_FILE_URL - "URL of your Config.env file" 
  You can also upload your config file on gdrive and use index link
- After that go to Action tab on your forked repo and run action"
- Your bot will be deployed, you can check logs of actions and heroku in case if you face any issue.
```

```
NOTE: If your app got suspended Just delete the app ASAP and Deploy again with same name
```
## More ways to Deploy
<details>
    <summary> Click Here For More Details </summary>

Deploying is pretty much straight forward and is divided into several steps as follows:
## Installing requirements

- Clone this repo:
```
if you dont know how to clone than learn it first
```

- Install requirements
For Debian based distros
```
sudo apt install python3
```
Install Docker by following the [official Docker docs](https://docs.docker.com/engine/install/debian/)

OR
```
sudo snap install docker
```
- For Arch and it's derivatives:
```
sudo pacman -S docker python
```
- Install dependencies for running setup scripts:
```
pip3 install -r requirements-cli.txt
```
</details>

## Generate Database
<details>
    <summary><b>Click Here For More Details</b></summary>

**1. Using ElephantSQL**
- Go to https://elephantsql.com and create account (skip this if you already have **ElephantSQL** account)
- Hit `Create New Instance`
- Follow the further instructions in the screen
- Hit `Select Region`
- Hit `Review`
- Hit `Create instance`
- Select your database name
- Copy your database url, and fill to `DATABASE_URL` in config

**2. Using Heroku PostgreSQL**
<p><a href="https://dev.to/prisma/how-to-setup-a-free-postgresql-database-on-heroku-1dc1"> <img src="https://img.shields.io/badge/See%20Dev.to-black?style=for-the-badge&logo=dev.to" width="160""/></a></p>

</details>

## Setting up config file

```
cp config_sample.env config.env
```
- Remove the first line saying:
```
_____REMOVE_THIS_LINE_____=True
```
Fill up rest of the fields. Meaning of each field is discussed below:
### Required Field
- `BOT_TOKEN`: The Telegram Bot Token that you got from [@BotFather](https://t.me/BotFather)
- `TELEGRAM_API`: This is to authenticate your Telegram account for downloading Telegram files. You can get this from https://my.telegram.org. **NOTE**: DO NOT put this in quotes.
- `TELEGRAM_HASH`: This is to authenticate your Telegram account for downloading Telegram files. You can get this from https://my.telegram.org
- `OWNER_ID`: The Telegram User ID (not username) of the Owner of the bot
- `GDRIVE_FOLDER_ID`: This is the folder ID of the Google Drive Folder to which you want to upload all the mirrors.
- `DOWNLOAD_DIR`: The path to the local folder where the downloads should be downloaded to
- `DOWNLOAD_STATUS_UPDATE_INTERVAL`: A short interval of time in seconds after which the Mirror progress/status message is updated. (I recommend to keep it to `7` seconds at least)  
- `AUTO_DELETE_MESSAGE_DURATION`: Interval of time (in seconds), after which the bot deletes it's message (and command message) which is expected to be viewed instantly. (**NOTE**: Set to `-1` to never automatically delete messages)
-`BASE_URL_OF_BOT`: (Required for Heroku to avoid sleep/idling) Valid BASE URL of app where the bot is deployed. Format of URL should be `http://myip` (where `myip` is the IP/Domain of your bot) or if you have chosen other port than `80` then fill in this format `http://myip:port`, for Heroku fill `https://yourappname.herokuapp.com` (**NOTE**: Do not put slash at the end), still got idling? You can use http://cron-job.org to ping your Heroku app.

### Optional Field
- `ACCOUNTS_ZIP_URL`: Only if you want to load your Service Account externally from an Index Link. Archive the accounts folder to a zip file. Fill this with the direct link of that file.
- `TOKEN_PICKLE_URL`: Only if you want to load your **token.pickle** externally from an Index Link. Fill this with the direct link of that file.
- `INDEX_URL`: Refer to https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index The URL should not have any trailing '/'
- `DATABASE_URL`: Your Database URL. See [Generate Database](https://github.com/arshsisodiya/helios-mirror-public#generate-database) to generate database (**NOTE**: If you use database you can save your Sudo ID permanently using `/addsudo` command).
- `AUTHORIZED_CHATS`: Fill user_id and chat_id (not username) of groups/users you want to authorize. Separate them with space, Examples: `-0123456789 -1122334455 6915401739`.
- `AUTHOR_NAME`: Telegraph Author Name, Default is "Helios Mirror Bot"
- `AUTHOR_URL`: Telegraph Author URL, Default is "https://t.me/heliosmirror"
- `TITLE_NAME`: Telegraph Title Name, Default is "Helios Mirror Search"
- `GD_INFO`: Google Drive File Discription, Default is "Uploaded by Helios Mirror Bot"
- `HEROKU_APP_NAME`: Your Heroku App name
- `HEROKU_API_KEY`: Heroku API Key
- `LOGS_CHATS`: Fill chat_id of channel/group where you want to store logs. Separate them with space, Examples: `-0123456789 -1122334455 6915401739`
- `LOG_CHANNEL`: File the chat_id of channel were you want leech dump, put channel ids which starts with -100xx , you can put multiple channel ids separate them with space <br> ```Note:Add Mirror bot in Log Channel(s)/Group(s) as Admin ```
- `CHANNEL_USERNAME`: Channel Username for Force Subscribe bot, it's disabled by default so if you want to use it you have to 
```python3 -m bot & python3 fsub.py in start.sh```
- 
- `MULTI_SEARCH_URL`: run driveid.py [here](https://github.com/arshsisodiya/helios-mirror-private/blob/helios-mirror/driveid.py). Upload **drive_folder** file [here](https://gist.github.com/). Open the raw file of that gist, it's URL will be your required variable.
**Note remove commit id from the link**

**Example:** <br> <br>
`Before: https://gist.githubusercontent.com/arshsisodiya/8cce4a4b4e7f4ea47e948b2d058e52ac/raw/19ba5ab5eb43016422193319f28bc3c7dfb60f25/gist.txt` <br> <br>
`After:  https://gist.githubusercontent.com/arshsisodiya/8cce4a4b4e7f4ea47e948b2d058e52ac/raw/gist.txt`

- `SUDO_USERS`: Fill user_id (not username) of users whom you want to give sudo permission. Separate them with space, Examples: `0123456789 1122334455 6915401739` (**NOTE**: If you want to save Sudo ID permanently without database, you must fill your Sudo Id here).
- `IS_TEAM_DRIVE`: Set to `True` if `GDRIVE_FOLDER_ID` is from a Team Drive else `False` or Leave it empty. `Bool`
- `USE_SERVICE_ACCOUNTS`: (Leave empty if unsure) Whether to use Service Accounts or not. For this to work see [Using Service Accounts](https://github.com/arshsisodiya/helios-mirror-public#generate-service-accounts-what-is-service-account) section below.
- `MEGA_API_KEY`: Mega.nz API key to mirror mega.nz links. Get it from [Mega SDK Page](https://mega.nz/sdk)
- `MEGA_EMAIL_ID`: Your E-Mail ID used to sign up on mega.nz for using premium account (Leave though)
- `MEGA_PASSWORD`: Your Password for your mega.nz account
- `BLOCK_MEGA_FOLDER`: If you want to remove mega.nz folder support, set it to `True`. `Bool`
- `BLOCK_MEGA_LINKS`: If you want to remove mega.nz mirror support, set it to `True`. `Bool`
- `STOP_DUPLICATE`: (Leave empty if unsure) if this field is set to `True`, bot will check file in Drive, if it is present in Drive, downloading or cloning will be stopped. (**NOTE**: File will be checked using filename not file hash, so this feature is not perfect yet). `Bool`
- `CLONE_LIMIT`: To limit the size of Google Drive folder/file which you can clone. Don't add unit, the default unit is `GB`.
- `MEGA_LIMIT`: To limit the size of Mega download. Don't add unit, the default unit is `GB`.
- `TORRENT_DIRECT_LIMIT`: To limit the Torrent/Direct mirror size. Don't add unit, the default unit is `GB`.
- `TAR_UNZIP_LIMIT`: To limit the size of mirroring as Tar or unzipmirror. Don't add unit, the default unit is `GB`.
- `VIEW_LINK`: View Link button to open file Index Link in browser instead of direct download link, you can figure out if it's compatible with your Index code or not, open any video from you Index and check if its URL ends with `?a=view`, if yes make it `True` it will work (Compatible with https://gitlab.com/ParveenBhadooOfficial/Google-Drive-Index Code). `Bool`
- `UPTOBOX_TOKEN`: Uptobox token to mirror uptobox links. Get it from [Uptobox Premium Account](https://uptobox.com/my_account).
- `IGNORE_PENDING_REQUESTS`: If you want the bot to ignore pending requests after it restarts, set this to `True`. `Bool`
- `STATUS_LIMIT`: Limit the no. of tasks shown in status message with button. (**NOTE**: Recommended limit is `4` tasks at max).
- `IS_VPS`: (Only for VPS) Don't set this to `True` even if you are using VPS, unless facing error with web server. `Bool`
- `SERVER_PORT`: Only For VPS even if `IS_VPS` is `False` --> Base URL Port
- `RECURSIVE_SEARCH`: Set this to `True` to search in sub-folders with `/list` (**NOTE**: This will only work with Shared-Drive ID or fill `root` for main Drive. Folder IDs are not compatible with it.)
- `TG_SPLIT_SIZE`: Size of split in bytes, leave it empty for max size `2GB`.
- `AS_DOCUMENT`: Default Telegram file type upload. Empty or `False` means as media. `Bool`
- `EQUAL_SPLITS`: Split files larger than **TG_SPLIT_SIZE** into equal parts size. `Bool`
- `CUSTOM_FILENAME`: Add custom word to leeched file name.
- `PHPSESSID` and `CRYPT`: Cookies for gdtot google drive link generator. Check setup [here](https://github.com/arshsisodiya/helios-mirror-public#gdtot-cookies)
- `SHORTENER_API`: Fill your Shortener API key.
- `SHORTENER`: Shortener URL.
Supported URL Shorteners:
```
exe.io, gplinks.in, shrinkme.io, urlshortx.com, shortzon.com, bit.ly,
shorte.st, linkvertise.com , ouo.io
- `YT_COOKIES_URL`: Youtube authentication cookies. Check setup [Here](https://github.com/ytdl-org/youtube-dl#how-do-i-pass-cookies-to-youtube-dl). Use gist raw link and remove commit id from the link, so you can edit it from gists only.
- `NETRC_URL`: Use this incase you want to deploy heroku branch from without filling `UPSTREAM_REPO` variable, since after restart this file will cloned from github as empty file. Use gist raw link and remove commit id from the link, so you can edit it from gists only.

```

### Add more buttons (Optional Field)
Three buttons are already added including Drive Link, Index Link, and View Link, you can add extra buttons, if you don't know what are the below entries, simply leave them empty.
- `BUTTON_FOUR_NAME`:
- `BUTTON_FOUR_URL`:
- `BUTTON_FIVE_NAME`:
- `BUTTON_FIVE_URL`:
- `BUTTON_SIX_NAME`:
- `BUTTON_SIX_URL`:

## Bot commands to be set in [@BotFather](https://t.me/BotFather)

```
mirror - Start mirroring
zipmirror - Start mirroring and upload as .zip
unzipmirror - Extract files
qbmirror - Start mirroring using qBittorrent
qbzipmirror - Start mirroring and upload as .zip using qb
qbunzipmirror - Extract files using qBittorrent
leech - Leech Torrent/Direct link
zipleech - Leech Torrent/Direct link and upload as .zip
unzipleech - Leech Torrent/Direct link and extract
qbleech - Leech Torrent/Magnet using qBittorrent
qbzipleech - Leech Torrent/Magnet and upload as .zip using qb
qbunzipleech - Leech Torrent and extract using qb
clone - Copy file/folder to Drive count - Count file/folder of Drive link
watch - Mirror yt-dlp supported link
zipwatch - Mirror playlist link and upload as .zip
leechwatch - Leech through yt-dlp supported link
leechzipwatch - Leech playlist link and upload as .zip
leechset - Leech settings
setthumb - Set Thumbnail
status - Get Mirror Status message
list - [query] Search files in Drive using new and interactive ui
search - [query] Search files in Drive using new and interactive ui
ts - [query] Search for torrents with installed qbittorrent search plugins
cancel - Cancel a task
cancelall - Cancel all tasks
del - [drive_url] Delete file from Drive
log - Get the Bot Log [owner/sudo only]
shell - Run commands in Shell [owner only]
restart - Restart the Bot [owner/sudo only]
stats - Bot Usage Stats
usage - to show heroku dyno usage [Owner only]
ping - Ping the Bot
help - All cmds with description
```

## Getting Google OAuth API credential file
- Visit the [Google Cloud Console](https://console.developers.google.com/apis/credentials)
- Go to the OAuth Consent tab, fill it, and save.
- Go to the Credentials tab and click Create Credentials -> OAuth Client ID
- Choose Desktop and Create.
- Use the download button to download your credentials.
- Move that file to the root of mirrorbot, and rename it to **credentials.json**
- Visit [Google API page](https://console.developers.google.com/apis/library)
- Search for Drive and enable it if it is disabled
- Finally, run the script to generate **token.pickle** file for Google Drive:
```
pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib
python3 generate_drive_token.py
```
## Deploying On VPS
<details>
    <summary><b>Click Here For More Details</b></summary>
**IMPORTANT NOTE**: You must set `SERVER_PORT` variable to `80` or any other port you want to use.

- Start Docker daemon (skip if already running):
```
sudo dockerd
```
- Build Docker image:
```
sudo docker build . -t mirror-bot
```
- Run the image:
```
sudo docker run -p 80:80 mirror-bot
```
### OR

### Using Docker-compose, you can edit and build your image in seconds:

**NOTE**: If you want to use port other than 80, change it in [docker-compose.yml](https://github.com/arshsisodiya/helios-mirror-public/blob/master/docker-compose.yml)

```
sudo apt install docker-compose
```
- Build and run Docker image:
```
sudo docker-compose up
```
- After editing files with nano for example (nano start.sh):
```
sudo docker-compose build
sudo docker-compose up
```
OR
```
sudo docker-compose up --build
```
- To stop Docker: 
```
sudo docker ps
```
```
sudo docker stop id
```
- To clear the container (this will not affect the image):
```
sudo docker container prune
```
- To delete the image:
```
sudo docker image prune -a
```
- Tutorial video from Tortoolkit repo
<p><a href="https://youtu.be/c8_TU1sPK08"> <img src="https://img.shields.io/badge/See%20Video-black?style=for-the-badge&logo=YouTube" width="160""/></a></p>
</details>


## Deploying on Heroku
- Deploying on Heroku with Github Workflow
<p><a href="https://telegra.ph/Heroku-Deployment-10-04"> <img src="https://img.shields.io/badge/Deploy%20Guide-blueviolet?style=for-the-badge&logo=heroku" width="170""/></a></p>

- Deploying on Heroku with heroku-cli and Goorm IDE
<p><a href="https://telegra.ph/How-to-Deploy-a-Mirror-Bot-to-Heroku-with-CLI-05-06"> <img src="https://img.shields.io/badge/Deploy%20Guide-grey?style=for-the-badge&logo=telegraph" width="170""/></a></p>

# Using Service Accounts for uploading to avoid user rate limit

<details>
    <summary><b>Click Here For More Details</b></summary>


For Service Account to work, you must set `USE_SERVICE_ACCOUNTS` = "True" in config file or environment variables.
**NOTE**: Using Service Accounts is only recommended while uploading to a Team Drive.

## Generate Service Accounts. [What is Service Account](https://cloud.google.com/iam/docs/service-accounts)
Let us create only the Service Accounts that we need. 
**Warning**: Abuse of this feature is not the aim of this project and we do **NOT** recommend that you make a lot of projects, just one project and 100 SAs allow you plenty of use, its also possible that over abuse might get your projects banned by Google.

**NOTE**: If you have created SAs in past from this script, you can also just re download the keys by running:
```
python3 gen_sa_accounts.py --download-keys project_id
```

**NOTE:** 1 Service Account can upload/copy around 750 GB a day, 1 project can make 100 Service Accounts so you can upload 75 TB a day or clone 2 TB from each file creator (uploader email).

**NOTE:** Add Service Accounts to team drive or google group no need to add them in both.

### Create Service Accounts to Current Project (Recommended Method)
- List your projects ids
```
python3 gen_sa_accounts.py --list-projects
```
- Enable services automatically by this command
```
python3 gen_sa_accounts.py --enable-services $PROJECTID
```
- Create Sevice Accounts to current project
```
python3 gen_sa_accounts.py --create-sas $PROJECTID
```
- Download Sevice Accounts as accounts folder
```
python3 gen_sa_accounts.py --download-keys $PROJECTID
```

### Another Quick Method
```
python3 gen_sa_accounts.py --quick-setup 1 --new-only
```
A folder named accounts will be created which will contain keys for the Service Accounts.

#### Add Service Accounts to Google Group
- Mount accounts folder
```
cd accounts
```
- Grab emails form all accounts to emails.txt file that would be created in accounts folder
```
grep -oPh '"client_email": "\K[^"]+' *.json > emails.txt
```
- Unmount acounts folder
```
cd -
```
Then add emails from emails.txt to Google Group, after that add this Google Group to your Shared Drive and promote it to manager.

#### Add Service Accounts to the Team Drive
- Run:
```
python3 add_to_team_drive.py -d SharedTeamDriveSrcID
```
</details>

# Multi Search IDs
To use list from multi TD/folder. Run driveid.py in your terminal and follow it. It will generate **drive_folder** file or u can simply create `drive_folder` file in working directory and fill it, check below format:
```
MyTdName folderID/tdID IndexLink(if available)
MyTdName2 folderID/tdID IndexLink(if available)
```

## Yt-dlp and Index Authentication Using .netrc File
For using your premium accounts in Youtube-dl or for protected Index Links, edit the netrc file according to following format:
For using your premium accounts in yt-dlp or for protected Index Links, edit the netrc file according to following format:
```
machine host login username password my_youtube_password
machine host login username password my_password
```
**Note**: For `youtube` authentication use [cookies.txt](https://github.com/ytdl-org/youtube-dl#how-do-i-pass-cookies-to-youtube-dl) file.

For Index Link with only password without username, even http auth will not work, so this is the solution.
```
machine example.workers.dev password index_password
```
Where host is the name of extractor (eg. Youtube, Twitch). Multiple accounts of different hosts can be added each separated by a new line.
Where host is the name of extractor (eg. Twitch). Multiple accounts of different hosts can be added each separated by a new line.

---
## Gdtot Cookies
To Clone or Leech gdtot link follow these steps:
1. Login/Register to [gdtot](https://new.gdtot.top)
2. Copy this script and paste it in browser bar
   ```
   javascript:(function () {
     const input = document.createElement('input');
     input.value = JSON.stringify({url : window.location.href, cookie : document.cookie});
     document.body.appendChild(input);
     input.focus();
     input.select();
     var result = document.execCommand('copy');
     document.body.removeChild(input);
     if(result)
       alert('Cookie copied to clipboard');
     else
       prompt('Failed to copy cookie. Manually copy below cookie\n\n', input.value);
   })();
   ```
   - After pressing enter your browser will prompt a alert.
3. Now you'll get this type of data in your clipboard
   ```
   {"url":"https://new.gdtot.org/","cookie":"PHPSESSID=k2xxxxxxxxxxxxxxxxxxxxj63o; crypt=NGxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxWdSVT0%3D"}
   ```
4. From this you have to paste value of PHPSESSID and crypt in config.env file.
