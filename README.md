xmobar-stocks
=============

quick and dirty perl script to show market info in xmobar.

## Synopsis ##

To run on the command line:

    xmobar-stocks "jpm$" "^ixic=NASDAQ%"

    JPM:<fc=#00ff00>34.37</fc> | NASDAQ:<fc=#ff0000>-0.86%</fc> | 

Thus, you can stick (something like) the following in your xmobarrc:


    Config { 
        -- ... 
        , commands = [
          -- obviously you can include other commands...
          , Run Com "/usr/bin/perl" ["/path/to/xmobar-stocks", "jpm$", "wf%", "gs+"] "stocks" 60
        ]
        , sepChar = "`"
        , template = " [ ... ]  `stocks` [ ... ] "
    }


## Description ##

Why not show some info about the markets in xmobar? This script lets you 
easily keep track of all the money you're losing. I cannot be held responsible
for any sadness that may arise from this realization (that you're losing
lots of money). 

I'm really not sure why this isn't built into xmobar, but oh well. This script
exists because I didn't want to have to recompile xmobar from source to add 
this functionality. Unless I'm missing something (likely: most things in Haskell
are a bit over my head), it seems like you need to recompile xmobar to add 
another plugin. This seems a little silly to me...

### Syntax ###
The syntax is as follows: 

    xmobar-stocks [ ... ]

It accepts a list of arguments in the following form:

    SYM[=alias]{$%+}

where: 

* SYM = stock symbol
* alias -- optional -- an optional alias to print instead of the symbol 
* {$%+}: Choose one (and only one) of these modifiers. 
  * $: ask [realtime] 
  * %: price change (%)
  * +: price change (absolute)

Thus: 

    "^ixic=NASDAQ%"

will yield the percentage change of NASDAQ and will be renamed to `NASDAQ` 
instead of `^ixic`.

### Customizing ###

The script is pretty short and self-explanatory. See the following for a
reference on the Yahoo finance API: http://www.gummy-stuff.org/Yahoo_data.htm

For convenience a few are listed here: 

* s = symbol
* o = open price
* b2 = ask (realtime)
* k2 = change % (realtime)
* c = change and % change
* p = previous close
* c1 = change
* p2 = percent change
* a = ask
