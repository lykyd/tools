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

**DNS record & nameservers**
- dig iloveclaude.com
- dig @ns1.registery iloveclaude.com (what this name server has for record)
- dig <url>: what this name server has for record
- nslookup <IP>: give name of the host
- whois <namehost>: all infos about host

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

Create a redirect folder link
- ln -s /origin-folder /shortcut

**VIM**
- i : insert mode
- ECHAP :q! : force quit without saving
- /u : search

**Bower**
- install component: bower install --save angular-toArrayFilter
- enable component: add component in the dependencies list
- uninstall: bower uninstall angular-toArrayFilter

## Drush

- drush sql-dump > /destination/db.sql
- drush sql-dump -—result-file=dump.sql
- drush dl views --destination=profiles/myprofile/modules/views
- drush upwd --password="givememypasswordback" "admin" : reset password
- drush updb : update database
- drush dis <modulename> : disable module
- drush pm-list --type=Module --status=enabled : list module
- drush up rules : update Rules module
- drush up drupal : update Drupal Core

## Angular
### Directives examples
<pre>ng-controller = "StoreController as store";</pre>
<pre>ng-repeat = "product in store.products";</pre>
<pre>ng-click = "tab.tabSet(1)";</pre>
<pre>ng-class = "{ active: tab.isSet(2) }";</pre>
<pre>ng-show/ng-hide = "tab.isSet(1)";</pre>
<pre>ng-src = "image";</pre>
<pre>angular.module("root", [])
  .controller("index", ["$scope", function($scope) {
    $scope.$watch('factor', function(newValue) {
      $scope.product = newValue * 2;
    });
    $scope.factor = 6;
  }]);</pre>

### Custom directives
<pre>angular.module('timetilleventApp')
  .directive('eventList', function () {
    return {
      restrict: 'E',
      templateUrl: 'views/event-list.html',
      // link: function postLink(scope, element, attrs) {
      //   element.text('this is the eventList directive');
      // },
      controller: function($scope, $rootScope, $http) {
         ...Code here...
      },
      controllerAs: 'events'
    };
});</pre>

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

## PHP
### Render HTML
<pre>ob_start();
echo 'text to display';
ob_end_flush(); OR $output = ob_get_clean();</pre>

### Passage par référence (fonction peut modifier variable référencée)
<pre>function foo(&$var) {
  $var++;
}
$a=5;
foo ($a);
// $a vaut 6 maintenant</pre>

###POO
####Classes
=> entité regroupant variables (attributs) et fonctions (méthodes), définissant des objets
=> instanciation: servir d’une classe pour déclarer un objet
####Constructeur : public function __construct
=> initialiser attributs dès la création
=> utilise setter
####spl_autoload_register : charger classe dynamiquement
Constant : attribut de la classe (pas de l’objet) qui ne change jamais
=> declaration >   const VALUE = 2;      util >    Classe::VALUE
Static : fonction ou attribut de la classe pas appelé par l’objet
=> decl >   public static function name()   util >    Classe::name();
=> decl >   private static $id = 0;     util >   self::$id
####Heritage
=> class Fille extends Mere
=> redéclarer fonction mere :
<pre>public function gagnerExperience() {
    // On appelle la méthode gagnerExperience() de la classe parente
    parent::gagnerExperience();
}</pre>
####Classe abstraites
=> abstract class Personnage : empêche d'instancier la classe, c'est une classe modèle donc on veut juste instancier ses filles
=> classe finale est l'inverse, elle ne peut être héritée

- array_shift() : strip first value out of array
- array_pop() : strip last value
- array_splice($array, 2) : strip two entries
- in_array("string", $array)
- setcookie("name", $value); print $_COOKIE["name"]
- mysql_fetch_row() : retourne une ligne de requête sour forme array
- PDO::FETCH_ASSOC : retourne array indexé par nom de la colonne
- $fh = fopen('test.html', 'a'); : lecture écriture
- fwrite($fh, '<h1>Hello world!</h1>');
- fclose($fh);
- unlink('test.html'); : delete file
- unset : détruire variable
- "===" : comparaison sur les types
- rsort : tri array en sens inverse
- define("CONSTANT", "Bonjour le monde.");
- ereg_replace('four', '4', $string); : replace four par 4 dans le string


## Technologies
###MongoDB
- Base de données NoSQL dite orientée documents
- Pas besoin de scripts SQL
- Information modélisée en Json
- Grande quantité de données

###Node.js
- environnement bas niveau, creation de serveur
- modèle non-bloquant (fait une chose en attendant qu’une autre finisse)

###Yeoman
outil générer un système et workflow pour le développement d’une web app

###Grunt
taskrunner de centaines de plugin pour automatiser des actions

###Drupal 8
- features remplacées par des fichiers config
- twig pour la gestion des templates
- composants Symfony2: le routing, dependencyInjection

###Drupal 7
Hook: fonction php
- hook_node_view : update affichage node
- hook_node_presave : update before save
- hook_node_load : update data while load
- hook_permission
- hook_menu : create url
- hook_theme : pour utiliser la fonction theme() in tpl files

Profile building with features and Profile2 module

###Git
Submodule : the parent keeps references of child git repositories
- bad with branches and remotes
- only track commits

Subtree : un seul dépôt

