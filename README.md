# .gitconfig
Here you can find the .gitconfig file I use at work :). Hope it helps you!

```sh
[user]
	name = Eduard Bargues
	email = ebargues@ohpen.com
[alias]
	; REBASE
	ra = rebase --abort
	rc = rebase --continue
	r-dev = "!git r dev"
	r-develop = "!git r develop"
	r-master = "!git r master"
	r = "!f(){ git fe; git rebase -i origin/\"$1\"; }; f"
	; CHECKOUT
	coh = "!f(){ git co hotfix \"$1\"; }; f"
	cob = "!f(){ git co bugfix \"$1\"; }; f"
	cof = "!f(){ git co feature \"$1\"; }; f"
	co = "!f(){ git checkout -b \"$1/$2\"; }; f"
	br = branch
	; COMMIT
	cp = cherry-pick
	cam = commit -a -m
	c-fixup = "!f() { git commit --fixup \"$(git rev-parse HEAD)\"}; f" 
	c-break = "!git c break:\"$1\""
	c-feat = "!git c feat:\"$1\""
	c-fix = "!git c fix:\"$1\""
	c = "!f(){ git commit -a -m \"$1\"; }; f"
	; LOG
	l = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all
	; PUSH
	puuf = push -u -f origin
	puf = push -f
	; CONFIGURATION
	egc = config --global -e
	elc = config --local -e
	esc = config --system -e
    ; TRAILERS
    thanks-to = "!git trailer-add Co-authored-by"
    requested-by ="!git trailer-add Requested-by"
    reported-by = "!git trailer-add Reported-by"
    tested-by = "!git trailer-add Tested-by"
    trailer-add = "!f(){ GIT_EDITOR=\"git interpret-trailers --trailer='$1: $2' --in-place\" git commit --amend; }; f"
    ; MIX
    st = status
    hurry-develop = "!git hurry develop"
    hurry-master = "!git hurry master"
    hurry = "!f(){ git fetch; git rebase -i origin/\"$1\" --autosquash; git push -f -u origin \"$(git branch --show-current)\" }; f"
[color]
    ui = true
[color "status"]
    changed = yellow bold
    untracked = red bold
    added = green bold
[core]
	editor = code --new-window --wait
[diff]
	tool = vscode-diff
[difftool]
	prompt = false
[difftool "vscode-diff"]
	cmd = code --wait --diff $LOCAL $REMOTE 
[merge]
	tool = vscode-merge
[mergetool]
	keepBackup = false
[mergetool "vscode-merge"]
	cmd = code --wait $MERGED
```
