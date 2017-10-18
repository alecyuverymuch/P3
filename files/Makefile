###
# This Makefile can be used to make a parser for the cimple language
# (parser.class) and to make a program (P3.class) that tests the parser and
# the unparse methods in ast.java.
#
# make clean removes all generated files.
#
###

JC = javac
CP = ~cs536-1/public/tools/deps_src/java-cup-11b.jar:~cs536-1/public/tools/deps_src/java-cup-11b-runtime.jar:~cs536-1/public/tools/deps:.
CP2 = ~cs536-1/public/tools/deps:.

P3.class: P3.java parser.class Yylex.class ASTnode.class
	$(JC)    P3.java

parser.class: parser.java ASTnode.class Yylex.class ErrMsg.class
	$(JC)      parser.java

parser.java: cimple.cup
	java   java_cup.Main < cimple.cup

Yylex.class: cimple.jlex.java sym.class ErrMsg.class
	$(JC)   cimple.jlex.java

ASTnode.class: ast.java
	$(JC)  ast.java

cimple.jlex.java: cimple.jlex sym.class
	java    JLex.Main cimple.jlex

sym.class: sym.java
	$(JC)    sym.java

sym.java: cimple.cup
	java    java_cup.Main < cimple.cup

ErrMsg.class: ErrMsg.java
	$(JC) ErrMsg.java

##test
test:
	java   P3 test.cimple test.out

###
# clean
###
clean:
	rm -f *~ *.class parser.java cimple.jlex.java sym.java
