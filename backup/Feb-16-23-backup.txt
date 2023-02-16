#!/bin/bash

# VAP - Virtual Assistant Petko

SCRIPT_DIR=$( cd -- "$( dirname -- "${BASH_SOURCE[0]}" )" &> /dev/null && pwd )
FILE_NAME=$(basename -- "$0")
FILE_PATH="${SCRIPT_DIR}/${FILE_NAME}"

BACKUPTIME=`date +%b-%d-%y` 
SCRIPT_DIR="$SCRIPT_DIR/backup/$BACKUPTIME-backup.txt"
cp $FILE_PATH $SCRIPT_DIR

DIR="${BASH_SOURCE%/*}"
if [[ ! -d "$DIR" ]]; 
then 
DIR="$PWD"; 
fi
. "$DIR/scripts/start.sh"

printf "${green}Zdrasti, $USER ${NC}"
echo " "
echo " "
printf "${yellow}"
cpu_temp=$(($(cat /sys/class/thermal/thermal_zone0/temp) / 1000))
temperature=$(($cpu_temp))
echo "cpu temperature : $temperature °C"
echo " "
echo " "

if [ $temperature > 30 ]
then
printf "${red} "
echo "      (               )      )      )     )          "
echo "      )\ )  *   )  ( /(   ( /(   ( /(  ( /(   *   )  "
echo " (   (()/(\` )  /(  )\())  )\())  )\()) )\())\` )  /(  "
echo " )\   /(_))( )(_))((_)\  ((_)\  ((_)\ ((_)\  ( )(_)) "
echo "((_) (_)) (_(_())   ((_)__ ((_)  _((_)  ((_)(_(_())  "
echo "| __|/ __||_   _|  / _ \\ \ / / | || | / _ \|_   _|  "
echo "| _| \__ \  | |   | (_) |\ V /  | __ || (_) | | |    "
echo "|___||___/  |_|    \___/  |_|   |_||_| \___/  |_|    "
echo "                                                     "
fi

echo " "
echo " "
printf "${yellow} "

read -p "Iskash li Petko Assistenta da produlji? y/n " -n 1 -r
echo  " "
if [[ ! $REPLY =~ ^[Yy]$ ]]
then
    exit 1
fi

printf "${green}"
echo -n "Napishi mi kak se kazvash: "

read name

sleep 1
echo " "
echo "Zdrasti pak $name"
echo "Az sum tvoqt virualen asistent Petko"

Year=`date +%Y`
Month=`date +%m`
Day=`date +%d`
Hour=`date +%H`
Minute=`date +%M`
Second=`date +%S`

echo " "
echo "Dnes sme: $Day-$Month-$Year"
echo "Chasa e: $Hour:$Minute:$Second"
echo " "
echo -n "Napishi mi kolko pari imash: "
read pari
echo " "
echo "Imash $pari pari"
echo " "
echo "Kolko pari iskash da ti izvadq?"
read izvadq
echo " "
echo "Izvadq $izvadq pari"
echo "Imash $pari pari"
echo "Imash $izvadq pari"
echo "Imash $pari pari"
echo " "
echo " "

for (( counter=10; counter>0; counter-- ))
do
echo "$counter pruchka"
done
printf "\n ${purple}"

echo " "
echo " "
echo " "
echo " ██████╗██╗  ██╗ █████╗ ██╗   ██╗"
echo "██╔════╝██║  ██║██╔══██╗██║   ██║"
echo "██║     ███████║███████║██║   ██║"
echo "██║     ██╔══██║██╔══██║██║   ██║"
echo "╚██████╗██║  ██║██║  ██║╚██████╔╝"
echo " ╚═════╝╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ "
echo "                                 "
echo "                                 "
echo "                                 "
echo "                                 "
echo "                                 "
echo "                                 "
echo "                                 "
echo "                                 "
echo -n "Terminiram se sled "

for (( counter=3; counter!=0; counter-- ))
do
echo -n "$counter "
sleep 1
done
echo " "
exit
kill -9 $PPID
 