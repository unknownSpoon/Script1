# Script1

📝 Script 1: Create testa.txt to testz.txt with Letter - Number

#!/bin/bash

letter=a
number=1

for i in {1..26}
do
    filename="test${letter}.txt"
    echo "$letter - $number" > "$filename"
    letter=$(echo "$letter" | tr "a-y" "b-z")
    number=$((number + 1))
done

echo "Files created!"

🌐 Script 2: SFTP Connect by Index (scwebusers.sh)

#!/bin/bash

host="php.scweb.ca"
users=("alice" "bob" "carol")

if [ $# -eq 0 ]; then
    echo "List of users:"
    for i in "${!users[@]}"; do
        echo "$i) ${users[$i]}"
    done
    echo "Run the script with a number to connect, like: $0 1"
else
    index=$1
    if [ "$index" -ge 0 ] 2>/dev/null && [ "$index" -lt ${#users[@]} ]; then
        user=${users[$index]}
        echo "Connecting to $host as $user..."
        sftp "$user@$host"
    else
        echo "Invalid number. Run the script without arguments to see the list."
    fi
fi

🧹 Script 3: Remove Retired Users from retiredemployees.txt

#!/bin/bash

if [ ! -f retiredemployees.txt ]; then
    echo "Error: File 'retiredemployees.txt' not found."
    exit 1
fi

while IFS= read -r username; do
    if id "$username" &>/dev/null; then
        echo "Removing user: $username"
        sudo userdel -r "$username"
        if [ $? -eq 0 ]; then
            echo "User $username removed successfully."
        else
            echo "Failed to remove user $username."
        fi
    else
        echo "User $username does not exist."
    fi
done < retiredemployees.txt

Change user omar’s password to sabri without input:

echo omar:sabri | chpasswd

Set password of Omar (interactive):

passwd omar

Create group Sabri:

groupadd Sabri

Add omar to Sabri group:

usermod -aG Sabri omar

Change owner of sales.txt to omar:

chown omar sales.txt

Set permissions on asd.txt to rw-r-----:

chmod u=rw,g=r,o= asd.txt
# OR:
chmod 640 asd.txt

Numeric equivalent of u=rwx,g=rw,o= (i.e. rwxrw----):

chmod 760 passwords.txt

Set umask to make default file permissions 664:

umask 002

SSH known_hosts file for user osabri:

/home/osabri/.ssh/known_hosts

SCP command to send sales.csv to remote server:

scp /data/home2/sales.csv osabri@sabri.com:/salesdept/admin

SSH with password in script (not key auth):

sshpass -p "P@$$word#" ssh osabri@pei.ca

Brace expansion to shorten mv command:

mv /home/student/projects/old/version1/report{.txt,_backup.txt}

Install btop package:

sudo apt install btop

Find package that provides helix executable:

apt-file search bin/helix

Install local tmux.deb file:

sudo dpkg -i tmux.deb

🎨 Terminal Text Formatting (with ANSI Escape Codes)

To print colored or formatted text:

echo -e "\033[<CODE>m<text>\033[0m"

Effect	Code
Bold	1
Underline	4
Inverted (reverse)	7
Reset (clear all)	0
Text Color	Code
Black	30
Red	31
Green	32
Yellow	33
Blue	34
Magenta	35
Cyan	36
White	37
Background Color	Code
Black BG	40
Red BG	41
Green BG	42
Yellow BG	43
Blue BG	44
Magenta BG	45
Cyan BG	46
White BG	47

Examples:

echo -e "\033[1mBold Text\033[0m"
echo -e "\033[4mUnderlined\033[0m"
echo -e "\033[32mGreen Text\033[0m"
echo -e "\033[41m\033[30mBlack on Red BG\033[0m"
