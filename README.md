brew install koekeishiya/formulae/skhd

2. Grant Accessibility Permissions
Since Skhd needs permission to control your keyboard and mouse:

Go to: System Settings > Privacy & Security > Accessibility
Add Skhd:
If Skhd isn’t listed, click +, go to /opt/homebrew/bin/skhd, and add it.
Enable Accessibility for Skhd.

// 

# Start on startup

touch ~/Library/LaunchAgents/com.koekeishiya.skhd.plist
nvim ~/Library/LaunchAgents/com.koekeishiya.skhd.plist

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.koekeishiya.skhd</string>

    <key>ProgramArguments</key>
    <array>
        <string>/opt/homebrew/bin/skhd</string>
    </array>

    <key>RunAtLoad</key>
    <true/>

    <key>KeepAlive</key>
    <true/>

    <key>StandardErrorPath</key>
    <string>/tmp/skhd.err</string>

    <key>StandardOutPath</key>
    <string>/tmp/skhd.out</string>
</dict>
</plist>


launchctl load ~/Library/LaunchAgents/com.koekeishiya.skhd.plist
launchctl list | grep skhd
launchctl stop com.koekeishiya.skhd
launchctl start com.koekeishiya.skhd
