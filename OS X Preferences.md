# Automatically install AppStore Applications and Updates
1. Automatically install AppStore applications and OS X Updates

		sudo defaults write /Library/Preferences/com.apple.commerce AutoUpdate -bool TRUE
		sudo defaults write /Library/Preferences/com.apple.commerce AutoUpdateRestartRequired -bool TRUE
2. Enable softwareupdate schedule

		sudo softwareupdate --schedule on
