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
Keywords used to construct a proof of a `Claim` under a `Premise` regarding a `Strategy` 

|Keyword|Explanation|Rule
|---|---|---|
| `assume`         | Introduce an assumption into the proof context                   | `Goal = A -> B` / `assume h : A` ⇒ `Γ, h : A ⊢ B`                              |
| `apply`          | Apply a theorem, lemma, or rule to the current goal              | `Γ ⊢ B`, `Γ ⊢ A -> B` ⇒ new goal `Γ ⊢ A`                                       |
| `have`           | Introduce an intermediate result                                 | `Γ ⊢ A`, `Γ, h : A ⊢ B` ⇒ `Γ ⊢ B`                                              |
| `show`           | Explicitly state the current subgoal                             | `show A` ⇒ current goal becomes `A`                                            |
| `split`          | Split a conjunction goal into separate goals                     | `Γ ⊢ A and B` ⇒ goals `Γ ⊢ A` and `Γ ⊢ B`                                      |
| `cases`          | Perform case analysis on a disjunction, enum, or sum type        | `Γ, h : A or B ⊢ C` ⇒ goals `Γ, h₁ : A ⊢ C` and `Γ, h₂ : B ⊢ C`                |
| `rewrite`        | Rewrite the goal using an equality                               | `Γ, h : a == b ⊢ P(a)` ⇒ `Γ ⊢ P(b)`                                            |
| `unfold`         | Expand a definition                                              | `Γ ⊢ f(x)` ⇒ replace `f` with its definition                                   |
| `simplify`       | Reduce expressions using built-in simplification rules           | `Γ ⊢ expr` ⇒ simplified form of `expr`                                         |
| `exists`         | Provide a witness for an existential goal                        | `Γ ⊢ exists x : T, P(x)` ⇒ provide `w : T`, new goal `Γ ⊢ P(w)`                |
| `induction`      | Perform induction over a recursive structure or time index       | `Γ ⊢ forall n, P(n)` ⇒ goals `Γ ⊢ P(0)` and `Γ, P(n) ⊢ P(n+1)`                 |
| `invariant`      | Introduce or apply an invariant over all reachable states        | `Γ ⊢ A G P` ⇒ prove `P` initially and that transitions preserve `P`            |
| `smt`            | Delegate the current arithmetic or logical goal to an SMT solver | `Γ ⊢ P` ⇒ succeeds if SMT proves `Γ ⇒ P`                                       |
| `modelcheck`     | Delegate a temporal property to the model checker                | `Γ ⊢ φ` ⇒ succeeds if the market model satisfies `φ` under the current premise |
| `counterexample` | Search for a path violating the current goal                     | `Γ ⊢ φ` ⇒ returns path `π` such that `π ⊭ φ`, or fails if none found           |
