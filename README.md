# Dev Tool

## Git
**Init repo**
- echo "# howhard" >> README.md
- git init
- git add README.md
- git commit -m "first commit"
- git remote add origin https://github.com/Laudanum/howhard.git
- git push -u origin master

**Create branch**
- git branch experimental-d3 => create local branch
- git push -u origin experimental-d3 => create the remote branch
- git push -u origin develop => in the remote to commit to develop

**Delete branch**
- local: git branch -D develop.romain
- remote: git push origin --delete develop.romain

**Reset last commit**
- git reset —-soft HEAD^ : go back to the previous but keep file changes
- git reset -—hard HEAD^ : go back to the previous and all changes
- git reset -—hard HEAD^^ : go back to 2 commits before
- git commit —-amend -m “New message” : add to the previous commit

**Hotfix**
- checkout hotfix
- commit & push
- checkout master
- pull
- merge hotfix & push
- git tag 0.2.8
- git push —-tags
- checkout develop
- pull
- merge hotfix & push

**Remote**
- git remote show origin : see local and remote branches relationship
- git remote prune origin : clean deleted remote branches

**Rebase**
- git fetch : get last commits from a remote (ex: origin/master) or a branch (ex: master)
- git rebase : stash our local commit, pull the remote, add the local commit on top
- git rebase —-continue  : continue rebase after fixing conflict (after git add)

**Interactive rebase**
- git rebase -i HEAD^3
Reorder commits
  reorder manually
Rename commit
  change ‘pick’ to ‘reword’
Split commits
  change ‘pick’ to ‘edit’
  - git reset HEAD^ : roll back last commit
  - git add co : not sure…
Squash commits
  change ‘pick’ to ’squash’ : will squash with upper commit in list
  enter new commit message

**Log, Compare and History**
- git log —-oneline
- git diff master develop : compare 2 branches
- git diff HEAD~2 : compare 2 last commits

**Cherry pick**
- git branch merge-request (create a branch where pick commits)
- git cherry-pick <commitnumber>
- OR git cherry-pick -n <commitnumber> : —no-commit option
- git reset (unstage all commit change)
- git checkout (what you don’t want)
- git commit and push
- git merge or rebase the branch from which picked with the one that picked

**No Merge (display)**
- git branch —-no-merge

**Reset**
- git reset origin/branchname —-hard 

**Alias**
- git config --global alias.co checkout
- git config --unset alias.lg

**Stash**
stashes staged and unstaged tracked files.
- git stash save
- git stash save —-keep-index : stash unstaged files only
- git stash save —-include-untracked : stash untracked files too
- git stash list : display stash in queue
- git stash list —-stat : more details on the stashed files
- git stash apply OR git stash apply stash@{2}: apply stash 0 by default except if we specify a number
- git stash drop : to remove the stash 0 from the queue (after stash apply)
- git stash pop : get last stash apply and drop it (if conflict you need to drop manually)
- git stash : to stash everything that james said is not committed
- git stash clear : delete all stashes

**Submodules**
create a repository on GitHub
- git submodule add git@example.com:css.git : create css directory
- git commit -m “Add CSS Submodule”
- git push
to modify the code of the submodule
- cd submodule directory
- git checkout master : submodule don’t have a branch by default
- git add co push
- cd .. : go to the parent directory
- git add co push
cloning a repository with submodule
- git submodule init : reference the submodules
- git submodule update : grad files of the submodules
pulling submodule last commits from
- git submodule update
if commit out of branch
- git ch master
- git merge conumber 
automatically push submodules
- git config alias.pushall ‘push --recurse-submodules=on-demand’

**Checkout a commit number**
- git checkout 8948d4f (commit number)

**Match remote with local branch**
- git branch —-set-upstream-to=origin/remotebranch localbranch

## Command line

**File creation and edition**
- touch file : create
- less file : display
- nano file : write

**SSH connexion**
- ssh username@www.domain.com
- ping www.domain.com => domain accessible
- telnet www.domain.com 22 => check access to ssh port
- telnet www.domain.com 80 => check access to web server port

**Rsync (connexion via ssh aux files)**
- rsync -vr -e “ssh -p numport” user@url-domain:dist/sources dist/local
- mysqldump dbname

**Secure copy (use ssh)**
- scp -P numport uname@urlname:/folder/file.sql ~/destination-folder/
- scp -r (folder and files inside)

**Permissions setup**
- groups : group that the user account belongs to
- chmod 755 file.ext

**MYSQL**
- mysqldump -uname -p dump.sql
- drop existing
- create schema
- mysql -uname -p dump.sql < db.sql

**Zip file**
- gzip file name

**Issue database**
- mv ib ibdata1.bak 
- cp -a ibdata1.bak ibdata1

**Import DB**
- USE database_name;
OR
- CREATE DATABASE database_name;
- USE database_name;

**Split DB**
- split -l 2000 ~/Desktop/dump.sql ~/Desktop/split_db/db-

**Screen**
- Ctrl+D, Ctrl+A
- screen -r pid (attache or detache)
- screen s NameofScreen
- screen ls (see the different jobs)
- Ctrl+D (kill the screen)

**GREP & TAIL**
- list of files: grep -Rl
- case insensitive: grep -i
or
- tail -f error.log (ctrl K to clean)

**DNS record**
- dig iloveclaude.com
- dig @ns1.registery iloveclaude.com (what this name server has for record)

**Direct message**
- ssh holly@wairarapa.local
- osascript -e 'display dialog "What?"'

**Restart Apache**
- sudo apachectl configtest &&  sudo apachectl restart

**Start Mysql**
- mysql -uroot
- mysql.server start

**Command shortcut**
- nano ~/.bash_profile
- source ~/.bash_profile
OR
- nano ~/.ssh/config

**Wget**
- wget --recursive --page-requisites --domains ozwayrealty.com.au --no-parent www.ozwayrealty.com.au/

**Patch**
- download .patch file
- patch -p1 < name.patch
OR
- git apply name.patch

**File/folder owner**
- sudo chown -R _www files/
_www: drupal
laudanum: user
root: ???

**Add RSA public key**
- less ~/.ssh/id_rsa.pub : copy that
- vi ~/.ssh/authorized_keys
- i
- paste key
- :x

**Copy RSA key**
- pbcopy < ~/.ssh/id_rsa.pub

## Drush

- drush sql-dump > /destination/db.sql
- drush sql-dump -—result-file=dump.sql
- drush dl views --destination=profiles/myprofile/modules/views
- drush upwd --password="givememypasswordback" "admin" : reset password
- drush updb : update database
- drush dis <modulename> : disable module
- drush pm-list --type=Module --status=enabled : list module

## Angular
### The Service Recipe
--- root.js<br>
<pre>angular.module("root", ["services"])
	.controller("index", ["$scope", "multiplier",
		function ($scope, multiplier) {
			$scope.product = multiplier.multiply(2);
		}]);</pre>
		
--- services.js<br>
<pre>angular.module("services", [])
	.value("factor", 6)
	.service("multiplier", ["factor", Multiplier]);</pre>
	
--- multiplier.js<br>
<pre>function Multiplier(valueFactor) {
	this.multiply = function (controllerFactor) {
		return valueFactor * controllerFactor;
	};
}</pre>

### The Provider Recipe
--- root.js<br>
<pre>angular.module("root", ["services"])
	.constant("messageText", "Hello world fringue !")
	.config(["messageProvider", "messageText", function (messageProvider, messageText) {
		messageProvider.setText(messageText);
	}])
	.controller("index", ["$scope", "message",
	function ($scope, message) {
		$scope.message = message.text;
	}]);</pre>
		
--- services.js<br>
<pre>angular.module("services", [])
	.provider("message", [function () {
		var text = null;

		this.setText = function (textString) {
			text = textString;
		};

		this.$get = [function () {
			return new Message(text);
		}];
	}]);</pre>
	
--- message.js<br>
<pre>function Message(text) {
	this.text = text;
}</pre>


