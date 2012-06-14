xmobar-stocks
=============

quick and dirty perl script to show market info in xmobar.

=head1 SYNOPSIS

    stocks "jpm$" "^ixic=NASDAQ%"

    JPM:<fc=#00ff00>34.37</fc> | NASDAQ:<fc=#ff0000>-0.86%</fc> | 

Stick (something like) the following in your xmobarrc:


    Config { 
        -- ... 
        , commands = [
          -- obviously you can include other commands...
          , Run Com "/usr/bin/perl" ["/path/to/xmobar-stocks", "jpm$", "wf%", "gs+"] "stocks" 60
        ]
        , sepChar = "`"
        , template = " [ ... ]  `stocks` [ ... ] "
    }


=head1 DESCRIPTION

Why not show some info about the markets in xmobar? This script lets you 
easily keep track of all the money you're losing. I cannot be held responsible
for any sadness that may arise from this realization. 

I'm really not sure why this isn't built into xmobar, but oh well. This script
because I didn't want to have to recompile xmobar from source to add this 
functionality. Unless I'm missing something (likely: most things in Haskell
are a bit over my head), it seems like you need to recompile xmobar to add 
another plugin. This seems a little silly to me...

=head2 Customizing

The script is pretty short and self-explanatory. See the following for a
reference on the Yahoo finance API: L<http://www.gummy-stuff.org/Yahoo_data.htm>

For convenience a few are listed here: 

=over 4

=item * s = symbol
=item * o = open price
=item * b2 = ask (realtime)
=item * k2 = change % (realtime)
=item * c = change and % change
=item * p = previous close
=item * c1 = change
=item * p2 = percent change
=item * a = ask
