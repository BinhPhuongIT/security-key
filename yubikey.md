MacOS SmartCard Locks System UP

1. Log into recovery mode
2. Open terminal
    mount -uw /Volumes/Macintosh\ HD
    mount -uw /Volumes/Data
    diskutil apfs list # to find uuid for /Volumes/Data
    /usr/bin/security filevault skip-sc-enforcement <uuid> set
3/ Reboot and login with password
4/ Open terminal
    sudo defaults write /Library/Preferences/com.apple.security.smartcard enforceSmartCard -bool false
    sudo defaults write /Library/Preferences/com.apple.security.smartcard allowUnmappedUsers -int 1

    if not work, please import profile with option
    <key>enforceSmartCard</key>
    <false/>

5/ Removing the Smart Card Pairing from macOS
    sc_auth list [username]
    sc_auth unpair -u [username]
    sc_auth unpair -h [hash]
    sc_auth unpair -u $(whoami)
    sc_auth pairing_ui -s disable 

ref: https://support.apple.com/en-us/101438
ref: https://support.apple.com/en-vn/guide/deployment/depfce8de48b/1/web/1.0
ref: https://support.yubico.com/hc/en-us/articles/360016649059-Using-your-YubiKey-as-a-smart-card-in-macOS
