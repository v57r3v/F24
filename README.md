java c
F24 ECE 551 
HW02, Due 11PM Thu. Sep. 19 
Pr. 1.
(a) Prove how the eigenvalues and eigenvectors of B ≜ A − 10I relate those of A ∈ FN×N .
(b) Describe (without proof) how the eigenvalues and eigenvectors of B ≜ αI +βA +γA2relate to those of A ∈ FN×N .
(c) Describe (without proof) how the eigenvalues and eigenvectors of B ≜ (αA + βI)−1relate to those of A ∈ FN×N , assuming the matrix in parentheses is invertible.
Hint. If A is invertible and Ax = λx, then multiplying both sides by (1/λ)A−1 yields (1/λ)x = A−1x.
Pr. 2. 
Let v1, v2, . . . , vN denote orthonormal vectors in RN . Let B denote the set of vectors {Av1, Av2, . . . , AvN } for A ∈ RN×N .
(a) Show that if A is an orthogonal matrix, then B is an orthonormal set.
(b) Show the converse: if B is an orthonormal set, then A is an orthogonal matrix.
Pr. 3. 
The Frobenius norm of an M × N matrix A is defined as  Express the Frobenius norm of A in terms of its singular values. Hint: First express |||A|||Fin terms of the matrix A′A.
Pr. 4. 
Let A be an M × N matrix with spectral norm σ1. Show the following bounds on the Frobenius norm:

The operator norm of a matrix equals its largest singular value σ1. The norm of a matrix can be measured many ways. The above inequality shows that if the Frobenius norm is small then the operator norm is as well. However, the operator norm being small does not guarantee that the Frobenius norm will be as well. (Think, for example, of the setting when M and N are very large).
Optional challenge: Is the upper bound tight?
Pr. 5. 
The Kronecker product of two matrices A ∈ Fm×n, B ∈ Fk×lis an important form. of “matrix multiplication” defined as follows:

Let vec(X) denote the “vectorize” operation that returns as its output a vector in FMN formed by stacking the N columns of X ∈ FM×N on top of each other.
For vectors x ∈ FM and y ∈ FN , so that xy⊤ ∈ FM×N , prove that

Verify (for yourself) by using commands vec(x * y’) and kron(y, x) in Julia for some real vectors, and using vec(x * transpose(y)) for some complex vectors.
(The equality above does not hold for vec(xy′) when y is complex.)
Pr. 6. 
Use an SVD of a square matrix A to describe a factorization A = QS where Q is unitary and S is positive semidefinite. Express Q and S in terms of the SVD components U, Σ and V of A.
Show that your Q and S satisfy the requirements.
(This matrix decomposition is analogous to the polar form. z = reiθ of a complex scalar z, where r is like S and eiθ is like Q.) Hint: V′V = I, so XY = XIY = XV ′V Y for compatible matrices.
Pr. 7. 
We use the notation F to denote either the field R of real numbers or the field C of complex numbers. This problem reviews what a field is. (See Ch. 1.)
Determine whether the following sets (with the usual senses of multiplication, addition, etc.) are fields or not. If the answer is Yes then you may say so without proof. If the answer is No then give a concrete counterexample for one of the defining properties of a field that is violated.
(a) The set of numbers that are irrational or zero, i.e., the set (R − Q) ∪ {0}
(b) The set of N × N diagonal matrices (where the “1” element is IN , and the “0” element is 0N×N ).
(c) The set of N × N diagonal matrices whose diagonal elements are either all zero or all nonzero.
(d) The set of rational functions, i.e., functions of the form. P(x)/Q(x) where P and Q are both polynomials (over the same field F) and Q is not zero.
(e) The set of N × N invertible matrices along with the N × N zero matrix.
Pr. 8. 
(a) Determine how eigenvalues and eigenvectors of

are related to singular values and singular vectors of A ∈ FN×N . In other words, if A = UΣV′, then express eigenvalues and eigenvectors of B in terms of components of U, Σ and V .
Hint. Start with some numerical experiments using self-generated A matrices and form. a conjecture.
Note that B is 2N × 2N.
Think about combining ui and viin various ways, such as ui ± vi, , and .
(b) Optional. Write a unitary eigendecomposition of B in matrix form.
(c) Optional. Generalize to the case A ∈ FM×N for M ≥ N.
This problem is related to one SVD numerical approach.
Pr. 9. 
Your graduate school experience should be more than just taking courses. To convince you that we really mean that, you have the opportunity to earn 30 HW points by writing down some of your own non-course-related goals for this semester. Thinking beyond courses is especially important in this (hopefully) post-pandemic period where self-care is crucial. In a few sentences or bullet points, list some of your personal non-course goals for this semester. The intent of this assignment is to encourage you to practice good self-care and encourage a growth-mindset. Examples of activities someone might list would be: going on a walk in your neighborhood N times a week, making connections with N new people, attending N CSP seminars to learn about current research, exploring some topic beyond what is required in the course just for your own interest, mastering a new recipe, reading a novel, etc. Hopefully your list will include some things that will help you relax and/or think about the bigger picture. There will be another HW problem at the end of the semester where we will ask you to reflect on your goals for the semester. If what you did was different than your proposal, please tell us what you ended up doing. Obviously we will never know if you actually read that novel or not. This is re代 写F24 ECE 551 HW02R
代做程序编程语言ally for you to be thinking about.
Pr. 10. 
(Finite difference matrix)
This problem develops a tool that will be used in a later HW for an application called photometric stereo. To approximate the derivatives of a function f(x) that is sampled on the grid x1, . . . , xn where xi+1 = xi + δ, a typical finite difference approach is:

When the sample spacing is δ = 1, this approximation simplifies to

We can express this relation for all xi samples via the matrix-vector product

where Dn is the so-called first finite difference matrix defined by

Here we choose to set Dn[n, 1] = 1, which corresponds to the (perhaps unexpected) approximation f′(xn) ≈ f(x1) − f(xn). This choice is called a periodic boundary condition because essentially we are assuming that the domain wraps around. We make this assumption because the resulting Dn is a circulant matrix so its eigenvectors can be computed in closed form! (See Ch. 8.)
The goal of this problem is for you to derive and implement the analog of Dn for 2D differentiation. Let f(x, y) be a function of two variables. We can approximate its partial derivatives using finite differences as follows:

To simplify notation, define the m × n matrices FXY, DFDX, and DFDY having elements as follows:

The x coordinate is along the column of FXY and the y coordinate is along the row of FXY, so we can think FXY[x,y]. Define corresponding vectors fxy, dfdx, and dfdy in Rmn to be vectorized versions of FXY, DFDX, and DFDY. With this notation, we can succinctly express equations (1) and (2) as

where A is a 2mn × mn matrix.
To help explain the notation, here is a concrete example:

(a) Find an expression for A in terms of the first difference matrices Dn, Dm, appropriately sized identity matrices, and appropriate Kronecker products of these matrices. Use periodic boundary conditions.
Hint: Start with m = n = 3. Look for ways to use Kronecker product(s) and the vec trick.
Hint: To make a 5 × 5 identity matrix use:
using LinearAlgebra: I
I(5)
(b) Once you have determined A, write the function first_diffs_2d_matrix that takes as input the dimensions m and n of FXY and returns the appropriate A matrix, stored in sparse format.
In Julia, your file should be named first_diffs_2d_matrix.jl and should contain the following function:
"""
A = first_diffs_2d_matrix(m, n)
# In:
- `m` and `n` are positive integers
# Out:
- `A` is a `2mn × mn` sparse matrix such that `A * vec(X)` computes the
first differences down the columns (along x direction)
and across the (along y direction) of the `m × n` matrix `X`.
"""
function first_diffs_2d_matrix(m, n)
Email your solution as an attachment to [email   protected].
Hint. Be sure to have using [packagename] at the top of your code for any package you use.
The matrix A can be gigantic. For example, suppose m = 550 and n = 430, then A is a 473, 000 × 236, 500 matrix that would require 833 GB of RAM if stored as a full double precision matrix! However, A has only 4mn nonzero entries, so it is very sparse.
Matrices with many zero-valued elements are quite common in applications. For normal arrays, Julia (and other languages) stores zeros in the same way it stores other numeric values, so having many zero elements can use memory space unnecessarily and can sometimes require extra computing time.
Sparse matrices provide an efficient way to store data that has a large percentage of zero elements. While full matrices internally store every element in memory regardless of value, a sparse matrix data structure stores only the nonzero elements and their row indices. Using sparse matrices can significantly reduce the amount of memory required for data storage.
In Julia, to create a sparse matrix somewhat similar to Dn above one can use either the spdiagm command:
using SparseArrays
n = 5
A = spdiagm(0 => 1:n, -1 => ones(n-1))
or a loop:
n = 5
A = spzeros(n,n)
for i in 1:n-1
A[i,i], A[i,i+1] = i, 1
end
You should try one or both of these out and modify one of them to prepare your answer. For details, see the SparseArrays documentation.
For any Julia assignment, you should always try to think of your own ways of testing your function before submitting to the auto-grader. You do get unlimited tries with the auto-grader, but using the feedback from the auto-grader is a poor way to debug. By designing your own tests, you can examine their output interactively and fix bugs more intelligently.
In this problem your function is designed to compute finite difference approximations to derivatives along x and y. If you create a m × n array X that is, say, a picture of a disk, then the finite derivatives will be mostly zero except near the edges of the disk. (This property is related to an image processing application called edge detection that is discussed in EECS 556.)
Here is Julia code for making a (digital/sampled) disk and showing pictures of FXY, DFDX, DFDY.
using MIRTjim: jim
using Plots: savefig
m = 30; n = 20; X = Float64.([(x-12)^2+(y-8)^2 < 5^2 for x in 1:m, y in 1:n])
dfdx = diff(X; dims=1)
dfdy = diff(X; dims=2)
jim(
jim(X, "FXY: f(x,y)"; xlabel="x", ylabel="y"),
jim(dfdx, "DFDX: df(x,y) / dx"; xlabel="x", ylabel="y"),
jim(dfdy, "DFDY: df(x,y) / dy"; xlabel="x", ylabel="y"),
) # savefig("hp074_disk.pdf")

You should make similar examples to test your function.







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
