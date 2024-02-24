# Cacher du texte dans une image
## Explication
Chaque image est représenté par une liste de triplet qui représente la quantité de rouge, de vert et de bleu dans chaque image.
[[23,25,6],[23,5,36],...
En stéganographie quand on veut cacher une information dans une image, la technique la plus répendu est de modifier les derniers bits des pixels.
En informatique, chaque chiffre peut être traduit en binaire par exemple:
232 = 11101000
81 = 1010001
29 = 11101
la couleur ressemble à ça :

![image](https://github.com/Saturnot/hide-text-in-image/assets/64526188/93fb5773-9078-4e61-9039-4f1cebd29539)

On peut ajouter autant de zéro que l'on veut devant ça ne changera pas la valeur (10111 = 0000000010111).
Dans une image classique chaque valeur du triplet contient 8 bits. Si on reprend donc notre exemple on a :
232 = 11101000
81  = 01010001
29  = 00011101

Si on modifie les 3 derniers bits de chaque valeur de rouge, de vert et de bleu, la couleur finale ne va pas changer beaucoup, ce changement sera quasiment invible à l'oeuil nu. C'est pour cela qu'on peut y stocker des informations. Maintenant il faut savoir ce qu'on va y stocker, moi je voulais stocker du texte, c'est pour ça que j'ai choisi d'utiliser l'ascii, qui est utiliser partout en informatique, elle asocie à chauqe caractère un chiffre que l'on peut convertire en binaire.
### Exemple : 
001100011 = c (minuscule)
Maintenant on peut diviser le "c" en 3 pour le cacher dans le premier pixel.
001100011 -> 001 100 011
On remplace la fin de chaque couleur (rouge, vert, bleu) par un "bout" du "c" ce qui donne :
11101000 -> 11101001 -> 233
01010001 -> 01010100 -> 84
00011101 -> 00011011 -> 27
la couleur modifiée ressemble donc à ça :

![image](https://github.com/Saturnot/hide-text-in-image/assets/64526188/474adb5a-8fcf-4e03-931c-cf5b5ddf0227)


