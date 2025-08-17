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

$G'$  Augmented grammar | $X$  Grammar symbol


LR-parsing Algorithm
---
```
INPUT: An input string w and an LR-parsing table with functions ACTION and GOTO for a grammar G

OUTPUT: If w is in L(G), the reduction steps of a bottom-up parse for w; otherwise, an error indication.

METHOD: Initially, the parser has S0 on its stack, where S0 is the initial state, and w$ in the input buffer.The parser then executes the program in following method

let 'a' be the first symbol of 'w$';
while(1) {
	let s be the state on top of the stack;
	if ( ACTION[s,a] =  shift t) {
		push t onto the stack;
		let a be the next input symbol;
	} else if ( ACTION[s,a] =  reduce A -> β) {
		pop |β| symbols off the stack;
		let state t now be on top of the stack;
		output the production A -> β;
	} else if ( ACTION[s,a] = accept) {
		break
	} else {
		call error-recovery routine;
	}
}
```
References
---
[Compilers, Pearson New International Edition, 2nd edition](https://www.pearson.com/en-gb/subject-catalog/p/compilers-pearson-new-international-edition/P200000003568/9781292037233)