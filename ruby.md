#Ruby

How to get 2 digits for a number : " permet d’avoir un résultat du style : 01:05:56 lorsqu’on compte les heures par exemple

#{format('%02d', hour)}:#{format('%02d', min)}:#{format('%02d', sec)}”
"#{hour.to_s.rjust(2, '0')}:#{min.to_s.rjust(2, '0')}:#{sec.to_s.rjust(2, '0')}

% meaning :

- `%w()` array of strings
- `%r()` regular expression.
- `%q()` string
- `%x()` a shell command (returning the output string)
- `%i()` array of symbols (Ruby >= 2.0.0)
- `%s()` symbol
- `%()` (without letter) shortcut for `%Q()`

[regxr.com](http://regxr.com) pour toutes les regx

##Change Ruby version
rvm use version
ou
rmv —default use 2.7.6

rvm list

##Parler au shell directement
Utiliser la commande system
system("pwd")

##Récupérer la data d'un site
curl -L www.thehackingproject.org

##Ouvrir un fichier
file = File.open("Gemfile", "a")
file.puts("gem 'pry'")
file.close

file = File.open("Gemfile", "r")
puts "Voici le contenu de ton Gemfile :"
puts file.read
file.close

##ARGV
ruby test.rb salut
dans lequel sont les lignes:
puts "Début du programme"
puts ARGV ==> va renvoyer "salut"
puts "Fin du programme"

##Ajouter tous les fichiers au require 
Pour add tout un chemin entier ‘(par exemple le dossier lib) aux require d’un programme ruby on peut simplement faire comme ceci :
require 'bundler'
Bundler.require

$:.unshift File.expand_path("./../lib", __FILE__)
require 'scrapper' #permet d'appeler le fichier scrapper sans avoir eu à ce sourier de l'appeler par son nom au dessus