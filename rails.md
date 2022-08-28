# Rails 

## Init
```ruby
rails new -d postgresql nomdelapp
bundle install
rails db:create ==> pour créer la db
```

## DBs
Pour générer une migration
```ruby
rails generate migration NomDeTaMigration 
```

Pour l'appliquer
```ruby
rails db:migrate 
```

Pour lancer PostGre :
```ruby
sudo service postgresql restart 
```

```ruby
rails db:drop
rails db:migrate
rails db:seed
```

## Routes
Dans le fichier routes pour créer une route vers une ressource :
```ruby
resources :nom_de_la_ressource
rails routes
```

Pour créer une route vers une ressource imbriquée dans une autre :
```ruby
resources :nom_de_la_ressource do
  resources :nom_de_la_ressource_enfant
end
```
Autres commandes :
```ruby
resources :nom_de_la_ressource, except: [:destroy]
resources :nom_de_la_ressource, only: [:new, :create, :index, :destroy]
```
ou encore
```ruby
resources :nom_de_la_ressource, only: %i[new create index destroy]
```
## Console
Si jamais la console refuse de se lancer
```ruby
bin/spring stop
```

## Controlers
How to generate a controller:
```ruby
rails generate controller ControllerName action1 action2
```
For instance:
```ruby
rails generate controller Greetings hello
```
This will generate a controller named greetings, a route greetings/hello, a view greetings, a view greetings/hello...

## Models
Comment générer un model
```ruby
rails generate model NomDeTonModel email:string is_admin:boolean
```

### Lier 2 modèles entre eux
#### Si aucun des 2 models n’existe
Création des modèles
```ruby
rails g model User first_name:string last_name:string age:integer city:string ==> création 1ere table
rails g model Article title:string subject:string content:text ==> création 2eme table
```
Lien entre les 2 modèles il faut modifier le fichier de migration dont les éléments appartiennent à une autre table
```ruby
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
```
Puis il faut migrer
```ruby
rails db:migrate
```



#### Si les 2 models existent
```ruby
rails generate migration AddIndexToArticles ==> on créé une migration
```
Puis on ajoute dans le fichier de migration cette ligne qui précise à quelle table on ajoute la reference key
```ruby

def change 
  add_reference :articles, :user, foreign_key: true
end
```
Et on migre 
```ruby
rails db:migrate
```
