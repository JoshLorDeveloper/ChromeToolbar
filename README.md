# ChromeToolbar
AppleScript program to make toolbar show and hide with mouse movement 

'''
set AppleScript's text item delimiters to ","
set tabHidden to false
repeat
	tell application "System Events"
		set activeApp to name of first application process whose frontmost is true
		if "Google Chrome" is not in (name of application processes) then exit repeat
	end tell
	set ycord to item 2 of every text item of (do shell script "/usr/local/bin/cliclick p") as integer
	if (ycord < 20) then
		if (tabHidden = false) then
			tell application "System Events" to keystroke "f" using {command down, shift down}
			delay 0.5
			set tabHidden to true
		end if
	else if (ycord > 125) then
		if (tabHidden = true) then
			delay 0.1
			set tabHidden to false
			tell application "System Events" to keystroke "f" using {command down, shift down}
		end if
	end if
	delay 0.5
end repeat
'''
