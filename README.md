## RofiFtw (Rofi for the web)

Use rofi to perform web search with instant search suggestions  </br>
As of now, it supports the following websites:</br>
* Youtube / Google 
* Deezer / Lastfm for music search
* Google books for books search (duh) </br>

with possibly more to come

### Requirements
* [rofi blocks ](https://github.com/OmarCastro/rofi-blocks)
 this is what makes the real-time interaction possible.
* [Jq](https://github.com/stedolan/jq) for Json processing.

### Usage
Simply run the wrapper script for whichever API you want to handle the request </br>
<i>Example:</i> </br>
` suggest youtube`  </br>

each of the APis can be run indpendently from your terminal: </br>
` youtube <search>`  </br> 
returns youtube suggestions of your entry in plain/text.  </br></br>
 ![scrot](https://raw.githubusercontent.com/BelkaDev/Rofiftw/master/src/scrot)</br>

you can configure each API in their own respective files. </br>
options can include search language and other basic search parameters. </br>

it's also made easy to add a custom API to the list, move them to the /APIs directory and follow the existing declarations.
#### Intercepting results
this script does nothing but to grab your selection which can seem to be pointless on its own. </br>

however, you can combine it with additional scripts to make things more interesting.</br> here is a non-exhaustive list of scripts that blend well with it.

* [play](https://github.com/BelkaDev/Mustream) songs/albums in Spotify
* [getbook](https://github.com/BelkaDev/scropts/blob/master/getBook) download publicly available books
* [youtubemenu](https://github.com/BelkaDev/scropts/blob/master/youtube) a youtube dmenu fetcher with thumbnails support

### Installation
```
git clone https://github.com/BelkaDev/RofiFtw.git ~/RofiFtw && cd ~/RofiFtw
chmod +x *
```
move the folder content to your $PATH directory

### Bugs & issues
* You may notice a small delay whilst processing the input</br>
this can be fixed by increasing the refresh rate but will affect the average response time.</br>
if you find a better workaround let me know
* special and non-utf characters cause rofi to break, so they are filtered by default. </br>
If you care about displaying them, [this fork](https://github.com/fogine/rofi-blocks/tree/fix-%233-wide-unicode) fixes the issues.
more instructions can be found in [the code](https://github.com/BelkaDev/RofiFtw/blob/master/handler)</br>

