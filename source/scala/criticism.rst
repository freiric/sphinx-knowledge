Scala collections why not

Type signature too complicated

Scala is complex: impredictable (is this bug), obscure it

Map signature simplified and got wrong, bug reported 44m

complicated signature to preserve type (bitset, sorted):

- composition of map breaks that
- map the identity ill-typed

java interop s broken (call scala map from java)

- java is broken


Scala complexities internals:

- no separate model from implementation
- cast and suppression of variance check
- implicit selection freeze any evolutoin of type inference
- inheritance of implementation
- filter recreates the collection

Type inference get it wrong:

- list of int and double return list of any
- variance and type inference made wrong, implicit contravariant parameter go the wrong way

Inheritance and immutability

- mutable operators on immutable collection: drop
- 24 slice methods

implementation details infest interface: 

- Set are extensionally and intensionnlly defined, with - and + op
- size op

Proposition
************

- define type instead of operation (Iso, Map, FlatMap)
- collections simplification: no mutable, no parallel, but Views always
- SizeInfo instead of size

