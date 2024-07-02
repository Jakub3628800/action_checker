# action_checker
Script to notify when github actions are finished.

# Dependencies
- gh cli
- notify-send

# Installation
Pick a directory where you want to install the script. (`~/.local/bin` in the example)

```bash
wget https://raw.githubusercontent.com/Jakub3628800/action_checker/master/action_checker.py -P ~/.local/bin && chmod +x ~/.local/bin/action_checker.py
```

# Running
You can ofcourse simply run the script with python installed on your system.
```bash
~/.local/bin/action_checker.py
```

Since I use `gh` cli to create pull requests, it's convenient to run `action_checker.py` after I create a pull request in the background.

To achieve that, add following function to your bash profile:
```bash
ghpr() {
	gh pr create
	exit_code=$?

	if [ $exit_code -eq 0 ]; then
    	echo "Firing up the PR checker in the background..."
    	~/.local/bin/action_checker.py &
	else
    	echo "Not running prchecker, pr create failed with exit code $exit_code"
	fi
}
```


dfsa