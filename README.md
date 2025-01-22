java c
F24 ECE 551
HW04, Due 11PM Thu. Oct. 03
Pr. 1.
(a) Prove the vec trick , i.e., for A ∈ FP ×M, X ∈ FM×N , B ∈ FN×Q. :
vec(AXB) = (B⊤ ⊗ A)vec(X),                                                       (1)
where vec(.) is the operator that stacks the columns of the input matrix into a vector, and ⊗ denotes the Kronecker product. Here we really mean transpose B⊤ even if B is complex valued!
(b) Suppose A, X, and B are all N × N dense matrices. Determine how many scalar-scalar multiplications are needed for the LHS vec(AXB) and compare to the number for the RHS (B⊤ ⊗ A)vec(X). Which version uses fewer?
One use of (1) is analyzing the 2D discrete Fourier transform. (DFT), which may be explored in later HW.
Pr. 2.
(Projection onto orthogonal complement of a 1D subspace)
(a) Determine an orthonormal basis for the orthogonal complement of the span of the vector   
(b) Determine an orthonormal basis for the orthogonal complement of the span of the vector   
(c) Determine (by hand, no Julia) the projection of the vector      onto the orthogonal complement of span({z}) without using the orthonormal basis you found in the previous part.
Hint. You may want to derive the general mathematical expression needed in the next part first, and then use that expression to solve this problem by hand.
(d) Write a function called orthcomp1 that projects an input vector y onto the orthogonal complement of span({x}) for an (nonzero) input vector x of the same length as y.
For full credit, your final version of the code must be computationally efficient, and it should be able to handle input vectors of length 10 million without running out of memory. Your code must not call svd or eig or I and the like. This problem can be solved in one line with elementary vector operations.
In Julia, your file should be named orthcomp1.jl and should contain the following function:
"""
z = orthcomp1(y, x)
Project `y` onto the orthogonal complement of `Span({x})`
# In:
* `y` vector
* `x` nonzero vector of same length, both possibly very long
# Out:
* `z` vector of same length
For full credit, your solution should be computationally efficient.
"""
function orthcomp1(y, x)
Email your solution as an attachment to [email   protected].
Test your code yourself using the example above (and others) before submitting to the autograder. Be sure to test it for very long input vectors.
(e) Submit your code (a screen capture is fine) to gradescope so that the grader can verify that your code is computa-tionally efficient. (The autograder checks only correctness, not efficiency.)
Pr. 3.
Let A be a diagonal matrix with real entries that are distinct and nonzero. Let x be a vector with all nonzero entries.
(a) Determine how the eigenvalues of the rank-1 update B = A + xx′ are related to the eigenvalues of A and the vector x. Your final expression must not have any matrices in it.
Hint. They will be implicitly代 写F24 ECE 551 HW04R
代做程序编程语言 related (not in a closed form. expression) as the solution of an equation involving the eigenvalues of A and the elements of x. Hint: G + H = G(I + G−1H) if G is invertible, and see HW1.
(b) Use your solution to the previous part to determine the eigenvalues of B when   
Hint: Julia’s Polynomials.jl package can be useful here.
Pr. 4.
(a) Show that f(x) = ∥Ax − b∥2 is a convex function on RN when matrix A has N columns.
Hint. Use the triangle inequality: ∥x + y∥2 ≤ ∥x∥2 + ∥y∥2 and the equality 1 = α + (1 − α).
(b) Show that the largest singular value of a matrix, i.e., the function σ1(X) : FM×N 7→ R, is a convex function of the elements of the M × N matrix X. Hint. Use the fact that σ1(X) = max∥u∥2=1 ∥Xu∥2. Also use these two basic properties of maxima / suprema: f(t) ≤ g(t) ⇒ maxt f(t) ≤ maxt g(t) and maxt (f(t) + g(t)) ≤ (maxt f(t)) + (maxt g(t)).
(c) (Optional.) Prove or disprove that the second singular value of a matrix, i.e., the function σ2(X) : FM×N 7→ R, is a convex function of the elements of the M × N matrix X when min(M, N) ≥ 2.
Pr. 5.
For A ∈ FM×N , b ∈ FM and x ∈ FN , show that (I − A+A)x and A+b are orthogonal vectors.
Hint. Use a compact SVD.
Non-graded problem(s) below
(Solutions will be provided for self check; do not submit to gradescope.)
Pr. 6.
Spherical manifold optimization problems
(a) Suppose A ∈ FM×N has rank 0 < r ≤ min(M, N) and SVD   
(1) xopt = arg max∥x∥2=1 ∥Ax∥2 = ?
(2) yopt = arg max∥y∥2=1 ∥A′y∥2 = ?
(3) When are xopt and yopt unique (to within a sign ambiguity)?
(4) Do answers change if you replace A with −A in the optimization problems? Explain why or why not.
(5) What constraints could you add to above manifold optimization problem (with the same objective function) so you get ur and vr?
(b) Suppose A ∈ FN×N is Hermitian, and has eigendecomposition      with descending eigenvalue ordering λ1 ≥ . . . ≥ λN ∈ R. Define: xopt = arg max∥x∥2=1 x′Ax.
(1) Prove that xopt = zv1 where |z| = 1.
(2) What is x′optAxopt?
(3) When is xopt unique (aside from the sign ambiguity)?
(c) Same A as in previous part. For some 1 < K ≤ r, define:

(1) Prove that xopt = zvK where |z| = 1, via an equivalent formulation involving projections.
(2) What is x′optAxopt?
(3) When is xopt unique (aside from the sign ambiguity)?
Pr. 7.
Suppose A ∈ FM×N with M ≥ N has full column rank, i.e., rank(A) = N.
Show, using an SVD of A, that A+ = (A′A)−1A′. When A is known to be full column rank, one could use this direct formula to compute the pseudoinverse instead of employing an SVD.
Pr. 8.
Consider the following set of three measurements (xi, yi): (1, 2), (2, 1), (3, 3).
(a) Find the line of the form. y = αx + β that best fits (in the 2-norm sense) this data.
(b) Find the line of the form. x = γy + δ that best fits (in the 2-norm sense) this data.
Hint. Re-use your answer from part (a).





         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
