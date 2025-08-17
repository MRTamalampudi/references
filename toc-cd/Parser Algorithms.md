Computation of Closure
---
$I$ is a set of items for a grammar $G$, then $CLOSURE(I)$ :

```
CLOSURE(I) {
	J=I;
	repeat
		for ( each item A -> ɑ.Bβ in J )
			for ( each production B -> γ of G)
				if ( B -> .γ is not in J)
					add B -> .γ to J;
	until no more items are added to J on one round;
	return J
}
```


Computation of LR(0) items:
---
```
void items(G'){
	C = {CLOSURE({[ S' -> .S ]})};
	repeat
		for ( each set of items I in C)
			for (each grammar symbol X)
				if ( GOTO(I,X) is not empty and not in C )
					add GOTO(I,X) to C;
	until no new sets of items are added to C on a round;
}
```


$G'$  Augmented grammar 
$X$  Grammar symbol

References
---
[Compilers, Pearson New International Edition, 2nd edition](https://www.pearson.com/en-gb/subject-catalog/p/compilers-pearson-new-international-edition/P200000003568/9781292037233)