# NNNFunction
This function is made to keep you in the place you left after using NNN, put it in your shell configration file


n ()
{

if [ -n "$NNNLVL" ] && ["${NNNLVL:-0}" -ge 1]; then 
echo "nnn is already running"
return
fi 

export NNN_TMPFILE="${XDG_CONFIG_HOME:-$HOME/.config}/nnn/.lastd"

nnn -Rd "$@"

if [ -f "$NNN_TMPFILE" ]; then 
      . "$NNN_TMPFILE"
      rm -f "$NNN_TMPFILE" > /dev/null

fi 

}

