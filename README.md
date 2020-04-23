# AutomatedFacebookBirthdayPosts
Using Apple Script run this in script editor or automator to tell your friends on facebook happy birthday. Buggy, but it works. Will want to have your facebook logged in on safari before hand. may need to give script editor, system events, automator, and more accessibility permission under system preferences. this takes control of your mouse and logs in and uses facebook as if it were a human. ill eventually learn a more effecient method of automating facebook stuff. Heres the script to coppy and paste in case the it doesnt show in the other file after download. Happens sometimes.

tell application "Safari"
	activate
	open location "https://www.facebook.com/events/birthdays/"
	close every window
	delay 1
	open location "https://www.facebook.com/events/birthdays/"
	delay 3
	
	
	tell application "System Events"
		click at {673, 373}
		keystroke "Happy birthday!"
		keystroke return
		delay 1
		keystroke "Happy birthday!"
	end tell
	delay 3
	quit
	return
end tell


on doWithTimeout(uiScript, timeoutSeconds)
	set endDate to (current date) + timeoutSeconds
	repeat
		try
			run script "tell application \"System Events\"
" & uiScript & "
end tell"
			exit repeat
		on error errorMessage
			if ((current date) > endDate) then
				error "Can not " & uiScript
			end if
		end try
	end repeat
end doWithTimeout
