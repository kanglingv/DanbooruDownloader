﻿Requirement:
=============================
- Windows XP or later.
- .Net Framework 4.0
- log4net 1.2.11 (newkey)
- HtmlAgilityPack 

For linux/Mac, you can try to compile the source code using:
- Mono (http://www.mono-project.com/Main_Page)
- SharpDevelop (http://www.icsharpcode.net/OpenSource/SD/Download/)

The latest source code can be pulled from https://github.com/Nandaka/DanbooruDownloader.
The compiled binary can be downloaded at http://nandaka.wordpress.com/tag/danbooru-batch-download/
The previous version of compiled binary can be downloaded at http://www.mediafire.com/?tglaujm3ylc88

DanbooruProvider.xml
=============================
This file will be parsed when you run the applications. You can modify the xml to add new provider.
The contents structure are:
- Name	: The name of the *booru.
- Url	: The root path of the *booru url, ie:http://danbooru.donmai.us
- QueryStringJson : For danbooru based, use:/post/index.json?%_query%
		    For gelbooru, not supported/no API provided.
- QueryStringXml  : For danbooru based, use:/post/index.xml?%_query%
             	    For gelbooru based, use:/index.php?page=dapi&amp;s=post&amp;q=index&amp;%_query%
- Preferred   : Xml/Json.
- DefaultLimit: Number of limit if not given.
- HardLimit   : Hard limit defined by server for each request.
- PasswordSalt: choujin-steiner--%PASSWORD%-- for danbooru.donmai.us.
- UserName    : Your username.
- Password    : Your password, in plain text.
- UseAuth     : true/false. Use authentication/login.


Filename Format
=============================
- %provider% 	= provider Name
- %id% 		= Image ID
- %tags% 	= Image Tags
- %rating% 	= Image Rating
- %md5% 	= MD5 Hash
- %artist% 	= Artist Tag
- %copyright% 	= Copyright Tag
- %character% 	= Character Tag
- %circle% 	= Circle Tag, yande.re extension
- %faults% 	= Faults Tag, yande.re extension
- %originalFilename% = Original Filename
- %searchtag% 	= Search tag

If the given tags is not available, it will replaced with empty string.

Settings
=============================
- Application Settings:
“Minimize to System Tray” => Minimize to system tray :D
“Auto Focus Currrently Downloaded” => Move the selected row to the currently downloaded image in Download List tab.
“Enable Logging”   => Enable general logging.
“Use Colored Tags” => Enable colored tags in Main Tabs.
"Use Global Tags.xml" => Only use tags.xml as the tags source.
                      If disabled, it will try to load tags-{provider_name}.xml as the source tags.xml.

- Tagging:
“Artist” [5]     => Limit number of Artist tags to be used in the filename format for %artist%.
“Copyright” [5]  => Limit number of Copyright tags to be used in the filename format for %copyright%.
“Character” [5]  => Limit number of Character tags to be used in the filename format for %character%.
“Circle” [5]     => Limit number of Circle tags to be used in the filename format for %cirle%.
“Faults” [5]     => Limit number of Faults tags to be used in the filename format for %faults%.
                    Double click to change the tags color.

“Blacklisted tags” => Tags to be blacklisted in the Main Tab/Batch Job. 
                      It will shown with grey background in Main Tab.
                      It will be skipped in Batch Job.
                      Separate each tag with new line.
“Ignored Tags”     => Tags to be ignored in the filename.
                      Separate each tag with new line.
“Use Regex” => Enable regular expression for filter Blacklisted/Ignored tags.

“Use Tags Auto Complete #” [200] => Enable Autocomplete in Tag searchbox in Main tab.
                                    Up to 200 tags will be retrieved. This is based on your tags.xml.
“Empty Tag Repl.” [____] => For filename formatting, for example you use %artist% meta for filename format 
                            but the image doesn't have this information, then it will replaced based on this value.

FAQ
=============================
Q1: I cannot download from Danbooru (403 Forbidden)!
A1: Please read http://danbooru.donmai.us/forum/show/72300.
    You need to supply login information in the DanbooruProvider.xml and set UseAuth to true.

Q2: I cannot download/can only download 1 image from 3DBooru!
A2: On Settings tab, check Pad User Agent.

Q3: I cannot use space in batch download, the program always converting it to underscores!
A3: Use '+' for space.

Q4: I got 503 error from Danbooru!
A4: See A1. If still have the error, see this: http://danbooru.donmai.us/forum/show/24011.

Q5: I got 'ERROR_MESSAGE_HERE'!
A5: Sent me a message in the comment with the details, such as:
    - The Provider you are using.
    - The query.
    - The settings (screen shot is fine, please upload it to http://imgur.com/)
    - The error message (screen shot also fine)

Q6: I got a lot of skipped files when do batch download!
A6: It is caused of the target filename is already exists. Add %md5% in your filename format.

Supported Board
=============================
Currently only supporting Danbooru-type, Gelbooru-type with Danbooru API,
and Shimmie2 with RSS enabled.
For Sankaku-related board, using HTML parser.

- danbooru (http://danbooru.donmai.us)				NSFW
- Sankaku Complex (http://chan.sankakucomplex.com)		NSFW
- Sankaku Complex (Idol) (http://idol.sankakucomplex.com)	NSFW
- Konachan (http://konachan.com)				NSFW
- oreno.imouto.org (http://oreno.imouto.org)			NSFW
- gelbooru.com (http://gelbooru.com)				NSFW
- nekobooru.net (http://nekobooru.net)				NSFW
- safebooru (http://safebooru.org)
- ichijou (ichijou.org)
- TheDoujin.com (http://thedoujin.com)				NSFW
- 3dbooru (http://behoimi.org)
- e621 (http://e621.net)					NSFW, Furry
- rule34 (http://rule34.xxx)					NSFW
- dollbooru
- 4chanhouse
- fairygarden
- NIS ImageBoard (http://nis.tinybooru.com)
- 3dBooru (http://behoimi.org)

License Agreement
=============================
Copyright (c) 2012, Nandaka
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, 
are permitted provided that the following conditions are met:

  - Redistributions of source code must retain the above copyright notice, this 
    list of conditions and the following disclaimer.
  - Redistributions in binary form must reproduce the above copyright notice, 
    this list of conditions and the following disclaimer in the documentation 
    and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND 
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED 
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE 
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR 
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS 
OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY 
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING 
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN 
IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
