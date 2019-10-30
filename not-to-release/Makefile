doc:
	@echo "----------------------"
	@echo "make convert"
	@echo "make validate"
	@echo "----------------------"

convert:
	grew transform -grs grs/regularize_synt_into_fixed.grs -i fr_gsd-ud-dev.conllu -o ../fr_gsd-ud-dev.conllu
	grew transform -grs grs/regularize_synt_into_fixed.grs -i fr_gsd-ud-test.conllu -o ../fr_gsd-ud-test.conllu
	grew transform -grs grs/regularize_synt_into_fixed.grs -i fr_gsd-ud-train.conllu -o ../fr_gsd-ud-train.conllu

validate:
	python tools/validate.py --lang fr ../fr_gsd-ud-dev.conllu || true
	python tools/validate.py --lang fr ../fr_gsd-ud-test.conllu || true
	python tools/validate.py --lang fr ../fr_gsd-ud-train.conllu || true

run:
	grew transform -grs grs/l_on.grs -i fr_gsd-ud-dev.conllu -o tmp
	mv -f tmp fr_gsd-ud-dev.conllu
	grew transform -grs grs/l_on.grs -i fr_gsd-ud-test.conllu -o tmp
	mv -f tmp fr_gsd-ud-test.conllu
	grew transform -grs grs/l_on.grs -i fr_gsd-ud-train.conllu -o tmp
	mv -f tmp fr_gsd-ud-train.conllu
