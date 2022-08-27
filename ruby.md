# Ruby

## General use
How to get 2 digits for a number : " permet d’avoir un résultat du style : 01:05:56 lorsqu’on compte les heures par exemple
```ruby
"#{format('%02d', hour)}:#{format('%02d', min)}:#{format('%02d', sec)}"
```
Par exemple
```ruby
"#{hour.to_s.rjust(2, '0')}:#{min.to_s.rjust(2, '0')}:#{sec.to_s.rjust(2, '0')}"
```

% meaning :

- `%w()` array of strings
- `%r()` regular expression.
- `%q()` string
- `%x()` a shell command (returning the output string)
- `%i()` array of symbols (Ruby >= 2.0.0)
- `%s()` symbol
- `%()` (without letter) shortcut for `%Q()`

[regxr.com](http://regxr.com) pour toutes les regx

## Change Ruby version
```shell
rvm use "la version désirée"
```
ou
```shell
rvm —default use "la version désirée"
```
Pour connaître la liste des versions installées :
```shell
rvm list
```

## Parler au shell directement
Utiliser la commande system
```ruby
system("pwd")
```

## Récupérer la data d'un site
```
curl -L www.thehackingproject.org
```

## Ouvrir un fichier
```ruby
file = File.open("Gemfile", "a")
file.puts("gem 'pry'")
file.close
```
```ruby
file = File.open("Gemfile", "r")
puts "Voici le contenu de ton Gemfile :"
puts file.read
file.close
```

## ARGV
On peut run un fichier ruby test.rb de cette façon:
```ruby
ruby test.rb salut
```
dans ce fichier on trouve les lignes

```ruby
puts "Début du programme"
puts ARGV
puts "Fin du programme"
```
Ce programme va alors nous renvoyer :
```ruby
Début du programme
salut
Fin du programme
```

## Ajouter tous les fichiers au require 
Pour add tout un chemin entier ‘(par exemple le dossier lib) aux require d’un programme ruby on peut simplement faire comme ceci :
```ruby
require 'bundler'
Bundler.require
```
Puis
```ruby
$:.unshift File.expand_path("./../lib", __FILE__)
require 'scrapper' #permet d'appeler le fichier scrapper sans avoir eu à ce sourier de l'appeler par son nom au dessus
```