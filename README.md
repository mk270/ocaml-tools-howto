Install OCaml from source
-------------------------

* download [ocaml-4.00.1.tar.gz](http://caml.inria.fr/distrib/ocaml-4.00/ocaml-4.00.1.tar.gz)
* tar zxvf path/to/ocaml-4.00.1.tar.gz 
* cd ocaml-4.00.1
* ./configure -prefix $HOME
* make world
* make bootstrap
* make opt
* (umask 022 && make install)

Install OPAM
------------

* git clone https://github.com/OCamlPro/opam
* cd opam
* ./configure --prefix=$HOME
* make
* make install
* opam init

Set up shell to use opam, by adding

  which opam > /dev/null && eval $(opam config -env)

to ~/.bashrc; in a fresh shell, run

* opam switch 4.00.1

The latter command appears to download and install a fresh OCaml compiler(!)


Install OCamlFind
-----------------

* opam install ocamlfind

Create a project
----------------

* mkdir foo && cd foo
* touch _tags
* touch helloworld.ml

Configure _tags with the library I am going to use, in my case:

  true: package(expat)

and remember to install the library with OPAM; the name of the package in _tags is not guaranteed to be the same as the name of the package as presented to OPAM; you'll need to fiddle with "ocamlfind list" and "opam search" to get this to line up

Run ocamlbuild
--------------

* ocamlbuild -use-ocamlfind helloworld.native

Note that by convention, you add ".native" in place of the ".ml" file you want at the bottom of your dependency graph.