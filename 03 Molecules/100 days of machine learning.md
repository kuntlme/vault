---
aliases:
tags:
  - molecule
Topics:
  - Machine Learning
---
#### index: [[2 Machine Learning]]
#### tags: #machinelearing #coding

# Types of Machine Learning

## 1. ![[Supervised Learning]]



---

## 2. [[Unsupervised Learning]]

---

## 3. [[Semi-Supervised Learning]]

---

## 4. ![[Reinforcement Learning]]


---

## NOTE

> ![[Labeled Data]]  
> ![[Unlabeled Data]]

---

# [[Supervised Learning]] Example

- Gathering the data pair of **(input, output - real number, label)**

## Example: Email Check (Spam or Not Spam)

- **Bag of Words** → way to convert text into a feature vector
- **Support Vector Machine (SVM) Algorithm** → represents the output label from human-readable form to number
- The algorithm plots all feature vectors on an imaginary hyperplane and separates:
    - Positive examples (e.g., spam)
    - Negative examples (e.g., not spam)
- The separator is called the **decision boundary**
  wx - b = 0,
  then machine make relation y = sign(wx - b)
  then find optimal value w* and b*
  f(x) = w*x - b*
  ![[Pasted image 20250819015837.png]]
  **margin** - We would also prefer that the hyperplane separates positive examples from negative ones with
  the largest margin. The margin is the distance between the closest examples of two classes,
  as defined by the **decision boundary**.
- **Statistical model / model** - the solution of optimization problem, given by w* and b*. The process of building is called **training**.
- here the separator is straight line so it is linear model.
# Notation and defination
- **Scalar** - only values (italic letter, like x or a)
- **Vector** - A vector is an ordered list of scalar values, called attributes. (bold character, for example, x or w)
ex - a = [2, 3]   here a<sup>(1)</sup> = 2 and a<sup>(2)</sup> = 3
- unordered collection -
	- including a & b -> [a, b]
	- excluding a & b -> (a, b)
- **NOTE** - R denote include from minus infinity to plus infinity.
- When an element x belongs to a set S, we write x ∈ S
- **intersection** - S3 <- S1 ∩ S2
- **union** - S3 <- S1 U S2
- **summation** - ∑
- **capital pi** -  Π  ( product of
elements)

- ### **Operations on Sets**
	A derived set creation operator looks like this: S Õ Ω {x2 | x œ S, x > 3}. This notation means
	that we create a new set S Õ by putting into it x squared such that that x is in S, and x is
	greater than 3.
	The cardinality operator |S| returns the number of elements in set S.
![[Pasted image 20250820013627.png]]
