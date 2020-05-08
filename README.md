## RofiFtw (Rofi for the web)

Use rofi to perform web search with instant search suggestions  </br>
As of now, it supports the following websites:</br>
* Youtube/Google 
* Wikipedia
* Duckduckgo
* Archwiki
* Amazon
* Deezer
* Lastfm (requires Api key)
* Google books
</br>


![demo](https://raw.githubusercontent.com/BelkaDev/Rofiftw/master/src/demo.gif)</br>

### Requirements
* [rofi blocks ](https://github.com/OmarCastro/rofi-blocks)
 this is what makes the rofi interaction dynamic.
* [Jq](https://github.com/stedolan/jq) for Json processing.

### Usage
Simply run the wrapper script for whichever API you'd want to handle the request </br>
<i>Example:</i> </br>
` suggest youtube`  </br>


Each of the APis can be run indpendently from your terminal: </br>
` youtube <search>`  </br> 
returns youtube suggestions of your entry in plain/text.  </br></br>
 ![scrot](https://raw.githubusercontent.com/BelkaDev/Rofiftw/master/src/scrot)</br>

you can configure all the APIs in their own respective files. </br>
options can include search language and other basic search parameters. </br> </br>
<b>note:</b> most of them barely include a basic search function, they aren't in any way complete </br>
it's not hard to implement more options by reading through their documentations. </br>
it's also made easy to add a custom API to the list, move them to the /APIs directory and follow the existing declarations.
#### Intercepting results
this script does nothing but to grab your selection which can seem to be pointless on its own. </br>

however, you can combine it with additional scripts to make things more interesting.</br> here is a non-exhaustive list of scripts that blend well with it.

* [play](https://github.com/BelkaDev/Mustream) songs/albums in Spotify
* [getbook](https://github.com/BelkaDev/scropts/blob/master/getBook) download publicly available books
* [youtubemenu](https://github.com/BelkaDev/scropts/blob/master/youtube) a youtube dmenu fetcher with thumbnails support

This is an example for handling the selection based on your search type, you can add it at the end </br>
of the wrapper script:

``` Bash
case "$API" in 
"google")  $BROWSER "https://www.google.com/search?q=$result" ;; 
"deezer" | "lastfm")  play "$selection" ;; 
"youtube") youtube "$selection" ;;
"books") getBook  "$selection" ;; 
esac
```

### Installation
```
git clone https://github.com/BelkaDev/RofiFtw.git ~/RofiFtw && cd ~/RofiFtw
chmod +x *
```
move the folder content to your $PATH directory

### Bugs & issues
* You may notice a small delay while processing the input:</br>
this can be fixed by increasing the refresh rate (ie number of typed characters before sending the request) </br> which will affect the average response time.</br>
At the time being it's linear and pretty straightforward.
if you know a better / more complex algorithm let me know.
* Special and non-utf characters cause rofi to break, so they are filtered by default. </br>
If you care about displaying them, [this fork](https://github.com/fogine/rofi-blocks/tree/fix-%233-wide-unicode) fixes the issues.
more instructions can be found in [the code](https://github.com/BelkaDev/RofiFtw/blob/master/handler)</br>

