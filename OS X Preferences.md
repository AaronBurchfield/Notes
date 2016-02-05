# Automatically install AppStore Applications and Updates
1. Automatically install AppStore applications and OS X Updates

		sudo defaults write /Library/Preferences/com.apple.commerce AutoUpdate -bool TRUE
		sudo defaults write /Library/Preferences/com.apple.commerce AutoUpdateRestartRequired -bool TRUE
		sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate AutomaticCheckEnabled -bool TRUE
		sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate AutomaticDownload -bool TRUE
		sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate CriticalUpdateInstall -bool TRUE
		sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate ConfigDataInstall -bool TRUE
2. Enable softwareupdate schedule

		sudo softwareupdate --schedule on
