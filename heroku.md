# Heroku

## Créer une app Heroku
```shell
heroku create nom-de-ton-app
heroku apps:rename nouveau-nom-de-ton-app ==> si besoin de renommer
```
Ensuite on la lance en ligne
```shell
git remote --v 
```
Cette commande devrait renvoyer quelque chose comme ça
```shell
heroku https://git.heroku.com/nom-de-ton-app.git (fetch)
heroku  https://git.heroku.com/nom-de-ton-app.git (push)
origin  git@github.com:username/repo.git (fetch)
origin  git@github.com:username/repo.git (push)
```
On peut alors l'upload en prod
```shell
git push heroku HEAD:master
```

Si on se retrouve avec une erreur car on essaie de push sur Heroku 22 et que la version de ruby n'est pas supportée on peut pousser sur heroku 20 à la place
```shell
heroku stack:set heroku-20
git push heroku HEAD:master
```
Enfin il faut push la db sur Heroku
```shell
heroku run rake db:migrate #nécessaire si l'application a une db
```

## Synthèse made in THP
```shell 
$ rails new myapp
$ cd myapp
$ heroku create un-nom-trop-cool
#Je change le Gemfile pour la BDD si je suis en SQLite3
$ bundle install
$ git add .
$ git commit -m "First commit and pushing to Heroku"
$ git push heroku master
$ heroku run rails db:migrate #optionnel si tu as une migration à migrer
```