# TP_VueJs Lancement 

```console
> cd vue-projet
```

```console
> npm install
```

```console
> npm run lint
```

```console
> npm run dev
```


Recoder libs formik 
Récolter de la data au sein d'un composant et les soummetres
Balise formik qui contient 3 propriétés 
onsubmit = @submit avec values  ave des states 

render fonction recup param qui viennent du composant parent
-> le faire en vue avec 4  slot props

Fonciton handlesubmit verif value ( tiens sur 6 lignes )
issubmitting l'éatat de la soumission passe a true avec handlsubmit

Injection de d'épendance => field 
automatiquement connecter a formik 
2 propriétés name et as ( chaine caractère composant html ou object custom input )

composant dynamique