# Sqlite 3

Pour SQL on va utiliser Sqlite 3. Pour l’installer :

```jsx
sudo apt-get install sqlite libsqlite3-dev
```

Ensuite on se déplace dans un dossier et on utilise la commande :

```jsx
sqlite3 db.sqlite
```

Pour sortir de sqlite c’est 
```jsx
ctrl D
```
Pour visualiser plus simplement le contenu via un SELECT * FROM on ajoute les headers
```jsx
.mode column
.headers on
```
Et on peut ensuite lister toutes les tables :
```jsx
.tables #liste toutes les tables
```
Exemple :
```jsx
SELECT * FROM TableName LIMIT 1; #retourne tous les headers
```