#Rails 

##Init
rails new -d postgresql nomdelapp
bundle install
rails db:create ==> pour créer la db

##DBs
Pour lancer PostGre :
sudo service postgresql restart 

Création de la DB :
rails db:create

rails db:drop
rails db:migrate
rails db:seed

##Routes
Dans le fichier routes :
resources :nom_de_la_ressource
rails routes

resources :nom_de_la_ressource do
  resources :nom_de_la_ressource_enfant
end

resources :nom_de_la_ressource, except: [:destroy]
resources :nom_de_la_ressource, only: [:new, :create, :index, :destroy]
ou encore
resources :nom_de_la_ressource, only: %i[new create index destroy]

##Console
Si jamais la console refuse de se lancer
bin/spring stop

##Models
rails generate model NomDeTonModel email:string is_admin:boolean

###Lier 2 modèles entre eux
####Si aucun des 2 models n’existe
rails g model User first_name:string last_name:string age:integer city:string ==> création 1ere table
rails g model Article title:string subject:string content:text ==> création 2eme table

class CreateArticles < ActiveRecord::Migration[5.2] ==> fichier de migration du 2eme model
  def change
    create_table :articles do |t|
      t.string :title
      t.string :subject
      t.text :content
      t.belongs_to :user, index: true ==> cette ligne rajoute la référence à la table users

      t.timestamps
    end
  end
end

rails db:migrate



####Si les 2 models existent
rails generate migration AddIndexToArticles ==> on créé une migration

def change ==> on ajoute dans le fichier de migration cette ligne qui précise à quelle table on ajoute la reference key
  add_reference :articles, :user, foreign_key: true
end

rails db:migrate
