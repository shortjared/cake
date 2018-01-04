# .PHONY: all
# all:

# compiles the template
#
# compiles via `yq` merge
compile:
	rm -rf .build && mkdir .build
	yq merge template/*.yml > .build/out.yml

# compiles and validates the template
validate: compile
	aws cloudformation validate-template --template-body file:///$$PWD/.build/out.yml

# watches all files, rebuilds, and validates on change
watch:
	@fswatch -o template | xargs -n1 -I{} mmake validate
