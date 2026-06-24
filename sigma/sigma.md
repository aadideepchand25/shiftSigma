## Strategies
Keywords used to construct a `Strategy` which describes a process between a stream of `Info` and a stream of `Action`

|Keyword|Explanation|Rule
|---|---|---|
|`->`|Function constructor
|`::`|Has-type relation
|`\|`|Case constructor
|`\`|Lambda function
|||
|`data`|Introduce new data type
|`where`|Introduce local function variable
|`class`|Introduce new class
|`instance`|Create member of class
|||
|`==`|Equality
|`=`|Assignment

## Models
Keywords used to construct a `Premise` which describes constraints of a market as well as a generative model.

- For now, a `Premise` only formulates a single-asset, frictionless market (ie. only concerns one asset's price and disregards nuances like transaction costs etc.)

|Keyword|Explanation|Rule
|---|---|---|
|`assume`|Make an assumption|
|`random`|Introduce a random variable
|||
|`for _ in _`|For loop
|`if _ then`|Conditional
|||
|`=`|Fixed assignment
|`~`|Distribution assignment
|`@`|Probability weight
|||
|`{ , }`|Distribution constructor

## Claims
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

## Proofs
Keywords used to construct a proof under