java c
F24 ECE 551
HW03, Due 11PM Thu. Sep. 26
Pr. 1.


(a) Let Q denote an M × K matrix having orthonormal columns.
Show that Q′Q = IK. Thus ∥Qx∥2 = ∥x∥2for all x ∈ CK.
(b) Show that the following converse is true:
if A is an M × K matrix for which ∥Ax∥2 = ∥x∥2for all x ∈ CK, then A′A = IK.
Your proof should be general enough to cover the case where A has complex elements.
Hint. Examine products with standard unit vectors ej and combinations like ej + ek, or consider an eigendecompo-sition of A′A − I.
Pr. 2.
Let A be an N × N Hermitian matrix with unitary eigendecomposition A = QΛQ′, where λ1 ≥ λ2 ≥ . . . ≥ λk ≥ 0 and 0 ≥ λk+1 ≥ . . . ≥ λN , for some 1 < k < N. Determine an SVD of A in terms of the given components.


Pr. 3.
The Ch. 3 notes show the following Venn diagram of matrices and eigendecompositions:





Each of the categories shown above is a strict superset of the categories nested with in it.
Provide example matrices A1, . . . , A5 that belong to the each of the categories above but not the next category nested within it. Try to provide the simplest possible example in each case.
For example, the matrix A1 = [0 1] is rectangular, but not square. Now you do A2, . . . , A5.
Hint. All the examples can be 1 × 1 or 2 × 2, often with simple “0” and “1” elements.




Pr. 4.
Let   
(a) Determine the null space of A, denoted by N (A), and the range space or column space of A denoted by R(A).
(b) Are they equal? Does your answer hold in general? If not, provide a counterexample.
Pr. 5.
Let A ∈ FM×N .
(a) Suppose W ∈ FM×M and Q ∈ FN×N are each unitary matrices.
Show that A and C ≜ W AQ have the same singular values.
Consequently, A and C have the same rank, the same Frobenius norm and the same operator norm. This is why the Frobenius norm and the operator norm are called unitarily invariant norms. Their value does not change when the matrix is multiplied from the left and/or the right by a unitary matrix. Any norm that depends only on the singular values of A will, by definition, be unitarily invariant.
(b) Suppose that W and Q are nonsingular but not necessarily unitary matrices. Do A and D ≜ W AQ have the same rank? Prove or give a counterexample.
(c) Continuing (b), do A and D = W AQ have the same singular values? Prove or give a counterexample.
Pr. 6.
Prove that the orthogonal complement of the range of a matrix A equals the null space of A′: R⊥(A) = N (A′).




Pr. 7.
Let A = xy′, where neither x nor y is 0.
(a) How many linearly independent columns does A have? I.e., of all the sets of columns from this matrix where the set is linearly independent, what is the maximum cardinality?
(b) What is the rank of A?
(c) Enter (cut and paste) this code into Julia:
using LinearAlgebra: svdvals
using Plots
using LaTeXStrings
n = 100
x = randn(n); y = randn(n); A = x*y'
s = svdvals(A)
scatter(s, yscale = :log10, label= "",
title = "singular values: log scale",
xlabel="i", ylabel=L"\sigma_i") # to make σi
(Ideally the ylabel should look like σi, but if it does not, it is OK. Comment out the ylabel part if needed.)
• How many numerically computed singular values of A are nonzero?
• What answer do you get when you type rank(A) ?
• Turn in your plot of the singular values and the answers.
You will have just seen that a theoretically rank-1 matrix will have multiple nonzero singular values when expressed in machine precision arithmetic; this property is due to roundoff errors (finite numerical precision). (Round-off errors should not be thought of as “wrong answers,” but just a fact of real-life computing to be understood and not feared.)
(d) To help locate the code for the rank function, type this into Julia:
@less rank(ones(3,2))
Examine the code for the rank function and write down the formula used to determine the threshold (aka tolerance) below which, due to roundoff errors, the code considers the singular value to be “zero.”
(e) Determine the numerical value of the threshold when A = [9 9].
(f) Optional. Check your answer to the previous代 写F24 ECE 551 HW03R
代做程序编程语言 part by using the Julia debugger to step into the rank function and examine the tolerance.
Pr. 8.
When D is an M × N (rectangular) diagonal matrix, its pseudoinverse D+ is an N × M (rectangular) diagonal matrix whose nonzero entries are the reciprocals 1/dk of the nonzero diagonal entries of D. A matrix A having SVD A = UΣV′ has A+ = V Σ+U′. Working with just this equality, determine by hand (experimenting / checking with code is OK) the pseudoinverse of
(a) A = xy′, where neither x ∈ FM nor y ∈ FN is 0, (your answer should depend only on x and y),
(b) A = xx′, where x ≠ 0.




Pr. 9.
(a) Find an orthonormal basis for the range of the M × N matrix that is all ones.
(b) Find an orthonormal basis for the range of   
(c) Find an orthonormal basis for the range of any 2 × 2 rotation matrix.
(d) Use the fact that R(A) = R(Ur) to modify the compact SVD code in §4.5 to write a function that returns an orthonormal basis for the range of a given matrix, akin to how nullspace returns a null space basis.
In Julia, your file should be named matrixrange.jl and should contain the following function:
"""
matrixrange(A::AbstractMatrix)
Return orthonormal basis matrix for the range of matrix `A`.
"""
function matrixrange(A::AbstractMatrix)
Email your solution as an attachment to [email   protected].
Check your code using your answers to the preceding parts.
(e) Optional. Find an orthonormal basis for the range of any 2 × 2 rotation matrix, such that the basis matrix has the smallest possible trace.
Non-graded problem(s) below
(Solutions will be provided for self check; do not submit to gradescope.)
Pr. 10.
Let A be a normal matrix of the (unnamed) type where each eigenvalue either has a different magnitude than all other eigenvalues, or has the same value as all other eigenvalues with its magnitude. In other words, having both |λj | = |λi| and λj = λiis not allowed. For example, A might have eigenvalues (3, 4ı, 4ı, −5) but cannot have eigenvalues (3, 4, 4ı, −5).
Prove that every right singular vector of A is also an eigenvector of A.
This problem finishes the story on relating SVD and eigendecomposition.
Pr. 11.
We write A ⪯ B iff B − A ⪰ 0, i.e., iff B − A is positive semidefinite.
For a > 0, determine   
Pr. 12.
Suppose that X = UxΣxVx′ and Y = UyΣyVy′ denote SVD s of the matrices X ∈ Fm×n and Y ∈ Fp×q.
(a) Show that
X ⊗ Y = (Ux ⊗ Uy)(Σx ⊗ Σy)(Vx ⊗ Vy)′
is an SVD of X ⊗ Y (up to a permutation of the singular values). The block diagonal matrix Σx ⊗ Σy contains the pairwise products of the singular values of X and Y .
Hint. First show that the formula is correct, then argue that it is an SVD by showing that Ux ⊗ Uy and Vx ⊗ Vy are unitary matrices.
Hint: You may find the following properties of Kronecker product useful:
• (X ⊗ Y )′ = X′ ⊗ Y′
• (X ⊗ Y )(W ⊗ Z) = (XW) ⊗ (Y Z)
(b) Now suppose that A = QaΛaQ′a and B = QbΛbQ′bare unitary eigendecompositions of the (normal) matrices A ∈ FN×N and B ∈ FM×M.
Show that
A ⊗ B = (Qa ⊗ Qb)(Λa ⊗ Λb)(Qa ⊗ Qb)′




is a unitary eigendecomposition of A ⊗ B. The diagonal matrix Λa ⊗ Λb contains the pairwise products of the eigenvalues of A and B.
Hint. First show that the formula is correct, then argue that it is an eigendecomposition by showing that Qa ⊗ Qb is a unitary matrix.
(c) Continuing (b), show that
A ⊕ B = (Qa ⊗ Qb)(Λa ⊕ Λb)(Qa ⊗ Qb)′
is an eigendecomposition of the Kronecker sum A ⊕ B ≜ (A ⊗ I) + (I ⊗ B), where you must determine the size(s) of the “I” in that expression. The diagonal matrix Λa ⊕ Λb contains the pairwise sums of the eigenvalues of A and B.
Hint. Start by writing IN = QaIN Q′a and IM = QbIMQ′bin the definition of A ⊕ B, and then apply (b).
Pr. 13.
Complete the “Introduction to Matrix Math” tutorial at https://pathbird.com/courses/register. (Use the registration code shown on the ECE 551 Canvas home page.) This tutorial should be helpful for anyone who wants deeper understanding of Julia for operations with matrices and vectors. Such operations are a major part of ECE 551.





         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
