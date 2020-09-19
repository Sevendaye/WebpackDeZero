### yarn add --dev webpack webpack-cli ###
a savoir: webpack-cli init : Permet de lancer la config de webpack (webpack.config.js)
### yarn add --dev @babel/core @babel/preset-env @babel/preset-react babel-loader ###

**Dans le fichier package.json**
scripts : {
    "build:prod": "webpack --mode production",
    "build:dev": "webpack --mode development"
}

**Ensuite on tape :**
1. *yarn build:prod*
2. *yarn build:dev*

### On crée in fichier .babelrc à la racine du projet ###

**On dit à webpack d'utiliser babel**

On ajoute "--module-bind js=babel-loader" au commande *"build:prod"* et *"build:dev"*


### On installe webpack-dev-server (pour le dev non pour la prod) ###
**yarn add --dev webpack-dev-server**
 On ajoute le **start:** package.json  
1. "start": "webpack-dev-server --open --mode development --module-bind js=babel-loader --content-base dist/"
  
### Ou bien on utilise le fichier webpack.config.js ###
module.exports = {
    mode: 'development',
    module: {
        rules: [
            { test: /\.js$/, use: 'babel-loader' }
        ]
    },
    devServer: {
        open: true,
        contentBase: 'dist',
    },
};

**ensuite dans package.json on change l'lobjet scripts:**
    "build": "webpack --mode production",
    "build:dev": "webpack",
    "start": "webpack-dev-server"

