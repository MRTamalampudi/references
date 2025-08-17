#### Computation of Closure
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
