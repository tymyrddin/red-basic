# Veil Installation error Failed to run (wine) Python pip pefile... Exit code: 1

In

# vi /usr/share/veil/config/setup.sh

Change line 587 to:

    sudo -u "${trueuser}" WINEPREFIX="${winedir}" wine "${winedir}/drive_c/Python34/python.exe" "-m" "pip" "install" "-Iv" "pefile==2019.4.18"

Then, run `# veil --setup` again.