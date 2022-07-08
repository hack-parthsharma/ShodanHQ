# Introduction

This is an nmap nse script to query the [Shodan](https://www.shodan.io) API and passively get information about hosts.

# Installation

Simple place the shodan-hq.nse script into your nmap scripts folder. e.g:

`cp shodan-hq.nse /usr/local/share/nmap/scripts/`

# Usage

Invoke the script like so:

`nmap --script shodan-hq.nse <target> --script-args 'apikey=<yourShodanAPIKey'`

You can set your Shodan API key in the shodan-hq.nse file itself to save you having to type it in every time:

```
-- Set your Shodan API key here to avoid typing it in every time:
local apiKey = ""
```

### Warning:
nmap will still scan the target host normally. If you only want to look up the target in Shodan you need to include the `-sn -Pn -n` flags. e.g:

`nmap --script shodan-hq.nse -sn -Pn -n <target>`

You could instead specify a single target with the `target` script argument. e.g:

`nmap --script shodan-hq.nse  --script-args 'apikey=<yourShodanAPIKey>,target=<hackme>'`


### Saving to file
The results can be written to file with the `outfile` script argument. e.g:

`nmap --script shodan-hq.nse -sn -Pn -n <target> -sn -Pn -n --script-args 'outfile=potato.csv'`

# Example output

Here we do a passive scan of a whole /24 range, giving -sV type output in under 20 seconds:

[![asciicast](https://asciinema.org/a/f0unqk9uxbe6yeu22zpqu5xgz.png)](https://asciinema.org/a/f0unqk9uxbe6yeu22zpqu5xgz)

# Help

```
nmap --script-help shodan-hq.nse
```
