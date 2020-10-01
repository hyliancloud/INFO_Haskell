# Haskell (INFO3)
## Listes

**Question 1: Expressions de Liste*
1. Une liste s’ecrit entre crochets, avec les éléements de la liste séparés par des virgules. Rappelez ce que font les operateurs ``[]``, ``:`` et ``++``.
* ``[]`` : Liste vide (aussi la fin de liste).
* ``:`` : Opérateur d'ajout d'un élément au début d'une liste.
* ``a ++ b`` : Concaténation de listes ; La première liste va être dupliquée et son dernier élément va pointer sur le premier élément de b.
2. Evaluez les expressions de liste suivantes :
```haskell
1:[2] -- [1, 2]
[3,4]++[1,2] -- [3, 4, 1, 2]
[3..10] -- [3, 4, 5, 6, 7, 8, 9, 10]
tail [1..4] ++ 5:[] -- [2, 3, 4, 5]
head [1..4] : [5] -- [1, 5]
reverse [1..4] ++ [5] -- [4, 3, 2, 1, 5]
1 : reverse [2..5] -- [1, 5, 4, 3, 2]
```
**Question 2: Définition de fonctions sur les listes**
1. Rappelez ce que font les fonctions suivantes définies dans ``prelude.hs`` :
* ``head`` : Retourne le premier élément de la liste.
* ``tail`` : Retourne la liste sans le premier élément.
* ``reverse`` : Inverse la liste.
* ``length`` : Retourne la longueur de la liste.
* ``drop`` : Prend en paramètre un entier N et une liste L et retourne L sans les N premiers éléments.
* ``take`` : Prend en paramètre un entier N et une liste L et retourne une liste avec les N premiers éléments de L.
* ``!!`` : Retourne l'élément de la liste avec l'indice indiqué.
* ``tails`` : Retourne une liste de listes contenant successivement les queues de chaque liste.
![alt text](Haskell_Caterpillar.PNG "Haskell Caterpillar")

2. La fonction ``last``, définie dans ``prelude.hs``, selectionne le dernier éléement d’une liste. Simulez dans ghci le comportement de last exclusivement a l’aide des fonctions :
```haskell
lst = [1, 2, 3, 4, 5]
```
* ``head`` et ``reverse``
```haskell
head (reverse lst)
```
* ``length`` et ``!!``
```haskell
lst !! (length lst - 1)
```
* ``head``, ``drop`` et ``length``.
```haskell
head (drop (length - 1) lst)
```
Donnez ensuite une version récursive de la fonction ``last``.
```haskell
last' :: [a] -> a
last' []			= error "empty list"
last' (_ : x : [])	= x
last' (_ : xs)		= last' xs

{- Teacher's reference
last' [] = error "*** Exception: last: empty list"
last' [x] = x
last' (_ : xs) = last' xs
-}
```

3. La fonction ``init``, definie dans ``prelude.hs``, supprime le dernier élément d’une liste. Simulez dans ghci le comportement de init exclusivement a l’aide des fonctions suivantes :
* ``take`` et ``length``
```haskell
take (length lst - 1) lst
```
* ``tail`` et ``reverse``
```haskell
reverse(tail (reverse lst))
```
* ``tails``, ``reverse`` et ``!!``
```haskell

```
Donner ensuite une version recursive de la fonction
```haskell
init' :: [a] -> [a]
init' []	= error "empty list"
init' [x] 	= []
init' (x : xs) = x : init' xs
```