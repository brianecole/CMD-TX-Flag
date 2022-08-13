Back in the DOS 3.22 era, my family had an IBM 5150 PC.  I cannot take credit for this creation, my dad had found someone at his work 
that used this, and he got a copy.  With the use of the ANSI.SYS driver, ESC codes, and text and background colors, a Texas flag could
be coded before the C:\>

TXPROMPT.TXT is the current iteration that is compatible with Windows 8 and higher (tested in Windows 10 and Windows 11), as well as in 
Virtual DOS environments running native MS-DOS all the way up to DOS 6.

In virtual machines or if you are running native MS or PC-DOS on bare metal, you will need to add the following line to your CONFIG.SYS

DEVICE=ANSI.SYS

And then add the following to your AUTOEXEC.BAT:
PROMPT $e[1m$e[K$_$e[1;44m*$e[0m$e[K$e[1;41m▀▀$e[0m $e[1;37m $h$P$e[1;37m$g$e[1;37m

For Windows 8 and higher set the PROMPT variable to:
$e[1;44m*$e[41m▀▀$e[0;1m $P$G

To change your Command prompt in Windows 8, go to Control Panel and Click on SYSTEM PROPERTIES.  

Windows 10 and 11 search from the START menu SYSTEM PROPERTIES

Make sure you are in the ADVANCED tab

Select ENVIRONMENT VARIABLES at the bottom right corner

Under the second heading, SYSTEM VARIABLES look for the Variable PROMPT.  If you do not see it, click NEW and then enter PROMPT for VARIABLE
and the desired code for the Prompt you want.

Description of what this is saying:
$e[		Escape code (ASCII code 27)
$e[xx;yy;zzm    Color attribute setting 
		xx = attribute code
		yy = foreground/character color code
		zz = background color code
		m = end of command
$e[1;44m	Set foreground/character color to bright white; set background color to Blue
*		The Texas Star
$e[41m		Set background color to red
▀▀              2x Extended ASCII code 223
$e[0;1m         Turn off bright; set foreground/characters to white
$P		Current Drive and Path
$G		">" symbol

After doing a little research for the color explaination above, my prompt doesn't appear to be complete, the escape sequences don't have all 
the required variables, however it does work as I want it in Windows 10 and 11, with the side affect that everything is bright white.

I don't mind this, but you can experiment with the following table:

Code 	Color
0 	Turn Off Attributes
1 	High Intensity
2 	Normal Intensity
4 	Underline (mono only)
5 	Blink
7 	Reverse Video
8 	Invisible
30 	Black
31 	Red
32 	Green
33 	Yellow
34 	Blue
35 	Magenta
36 	Cyan
37 	White
40 	Black
41 	Red
42 	Green
43 	Yellow
44 	Blue
45 	Magenta
46 	Cyan
47 	White