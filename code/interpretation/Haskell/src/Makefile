test:
	make 0-ConstAdd.test
	make 1-ZeroSucc.test
	make 2-ZeroSuccPred.test
	make 3-NB.test
	make 4-Lambda.test
	make 5-Letrec.test
	make 6-Monads.test
	make 7-Bananas.test

%.test:
	make $*.preprocess
	echo "main" | ghci -v0 -Wall -i../include preprocessed/$*.hs > log
	diff log $*/baseline
	rm -f log

%.ghci: 
	make $*.preprocess
	ghci -Wall -i../include preprocessed/$*.hs

%.preprocess:
	mkdir -p preprocessed
	cpp -P -I$* Template.hs preprocessed/$*.hs

clean:
	rm -f log
	rm -rf preprocessed

