## Models
Keywords used to construct a `Premise` which describes constraints of a market as well as a generative model.

- For now, a `Premise` only formulates a single-asset, frictionless market (ie. only concerns one asset's price and disregards nuances like transaction costs etc.)

|Keyword|Explanation|Rule
|---|---|---|
|`assume`|Make an assumption|
|`for _ in _`|For loop
|`if _ then`|Conditional
|||
|`S`|Price at a certain time| `t : Num` / `S(t) : Num`
|||
|`=`|Fixed assignment
|`~`|Distribution assignment
|`@`|Probability weight
|||
|`{ , }`|Distribution constructor

## Proofs
Keywords used to construct a `Claim` we can prove. A `Claim` will always be considered alongside a `Premise` which is a model of the market.
|Keyword|Explanation|Rule
|---|---|---|
|`forall`| For all values, a proposition holds | `(A : Prop) ∧ (D : Type)` / `(forall D : A) : Prop`
|`exists`| There is a value where  proposition holds | `(A : Prop) ∧ (D : Type)` / `(exists D : A) : Prop`
||||
|`->`| Implication | 
|`and`| Conjunction | `(A : Prop) ∧ (B: Prop)` / `A and B : Prop`
|`or`| Disjunction | `(A : Prop) ∧  (B: Prop)` / `A or B : Prop`
|`not`| Negation | `(A : Prop)` / `not A : Prop`
||||
|`==`| Equality | `(A : Num) ∧ (B: Num)` / `A == B : Prop`
|`>`| Greater Than | `(A : Num) ∧ (B: Num)` / `A > B : Prop`
|`<`| Less Than | `(A : Num) ∧ (B: Num)` / `A < B : Prop`
||||
|`A`| Property must hold for all paths | `p : Prop` / `A p : Prop`
|`E`| Property must hold for at least 1 path | `p : Prop` / `E p : Prop`
|`P`| Property must hold for p% of paths | `(p : Prop) ∧ (n : Num)` / `P n p : Prop`
|`X`| Property is true in next tick | `p : Prop` / `X p : Prop`
|`F`| Property will be true in a future state | `p : Prop` / `F p : Prop`
|`G`| Propety is true for all future states | `p : Prop` / `G p : Prop`
|`U`| Property is true until another is true | `(p : Prop) ∧ (q: Prop)` / `p U q : Prop`