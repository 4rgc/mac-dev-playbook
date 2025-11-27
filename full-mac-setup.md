# Full Mac Setup Process (for Andrii Bohdan)

There are some things in life that just can't be automated... or aren't 100% worth the time :(

This document covers that, at least in terms of setting up a brand new Mac out of the box.

## Initial configuration of a brand new Mac

Before starting, I completed Apple's mandatory macOS setup wizard (creating a local user account, and optionally signing into my iCloud account). Once on the macOS desktop, I do the following (in order):

- Log in to Apple ID
- Enable Touch ID in Preferences
- Copy fonts from old Mac (`~/Library/Fonts`)
- Install Ansible (following the guide in [README.md](README.md))
- Clone mac-dev-playbook to the Mac: `git clone git@github.com:4rgc/mac-dev-playbook.git`
- Run the playbook
  - If there are errors, you may need to finish up other tasks like installing 'old-fashioned' apps first (since I try to place Photoshop in the Dock and it can't be installed automatically). Then, run the playbook again ;)
- Open Brave through terminal with sync server
  - Hook into sync chain
  - Log into the Bitwarden extension
- Log into Bitwarden app
- Open Nextcloud, log in
- Open and enable privacy settings
  - Karabiner-Elements
  - Karabiner-EventViewer
  - Wacom Tablet
  - Logi Options+
  - Rectangle, disable Mac tiling
- Manually copy `~/Projects` and other folders in `~` from another Mac.
- Copy keychain items from old Mac using "Export items..." or manually for unexportable items.
- Copy ssh keys from old Mac (`~/.ssh`)
- Set up "Internet Accounts"
  - Use Bitwarden to get the account passwords
- `gh auth login`
- Install or complete setup for old-fashioned apps:
  - Wireguard
- Open Calendar and enable personal Google CalDAV/Nextcloud accounts.
- These things might be automatable, but I do them manually right now:
  - Configure Time Machine backup drive
  - Install Wireguard VPN configurations (if needed)

## Set up preferences

Crossed-out options are automated, but included for documentation.

- Set up preferences:
  - Keyboard
    - ~Key repeat rate -> ‘Fast’,~
    - ~Delay until repeat to ‘Short’~
    - ~Press ‘Globe’ key to -> ‘Change Input Source’~
    - ~Keyboard navigation -> On~
    - Keyboard shortcuts
      - Mission Control
        - Mission Control -> Off
        - Application windows -> Off
        - Move left a space -> Off
        - Move right a space -> Off
        - Create 7 more desktops
        - Restart System Preferences app, go back to Keyboard shortcuts
        - Switch to Desktop 1-8 -> On
      - ~Input sources~
        - ~Both on~
      - ~Accessibility~
        - ~Zoom -> On~
      - ~Function keys -> on~
      - ~Trackpad~
        - ~Scroll & Zoom -> Natural scrolling -> off~
    - ~Input sources -> “Canadian, Ukrainian, Japanese”~
    - ~Dictation Language -> English (Canada)~
  - Desktop & Dock
    - ~Automatically hide and show the Dock~
    - ~Stage manager -> On~
    - ~Show Widgets In stage manager -> Off~
    - ~Windows -> Close windows when quitting an application -> Off~
    - Mission Control -> Automatically rearrange Spaces based on most recent use -> Off
    - ~Mission Control -> When switching to an application, switch to a Space with open windows for the application -> On~
    - Shortcuts
      - Mission Control -> None
      - Application windows -> None
  - Screen Time -> Share Across Devices -> On
    - ~Turn display off on battery when inactive -> Never~
    - ~Turn display off on power adapter when inactive -> Never~
    - Show 24-hour time -> On
    - Show message when locked -> On
      - “Warning: Authorized Access Only This system is intended solely for use by authorized personnel. Unauthorized access, use, or dissemination of information is strictly prohibited and may result in severe consequences.”

## To Wrap in Post-provision automation

```
# SSH setup.
ssh-keygen  # and create a default key to set up .ssh folder
# TODO - Manually copy any shared SSH keys that are needed.
```

## When formatting old Mac

- Make sure anything new merged into `~/Dropbox/Apps/Config`:
  - Fonts from ~/Library/Fonts
- Follow Apple's guide [here](https://support.apple.com/en-au/HT212749)
