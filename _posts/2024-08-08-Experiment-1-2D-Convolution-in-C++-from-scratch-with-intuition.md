---
layout: post
title:  "Experiment #1 2D-Convolution in C++ from scratch with intuition"
date:   2024-08-08
last_modified_at: 2024-08-09
categories: [Experiments]
tags: [AI, Machine learning, Mathematics, C++]
---

<br/><br/>

# Personal introduction 
<br/>

<p style="text-align: justify;">
One of the experiments I really wanted to dig into personally was the convolution operations widely used not only in Signal processing but Artificial intelligence.
Those who have enough experience in any field related to Mathematics, have at least heard about convolutions, filters, or kernels. 
Such terms are so wildly used in those domains that it is difficult to not really have heard of them once. 
</p>
<br/>
<p style="text-align: justify;">
My motives for investigating this operation were not because they are famous only. I wanted to learn about them in deep but also observe <mark>how and why they are so 
useful</mark>, especially in Artificial intelligence as feature extraction techniques. 
</p>

<br/>
<p style="text-align: justify;">
So I decided to run several experiments on Convoltions. Not only one, but several which the current article constitutes the first one. 
</p>

<br/><br/>
## Intuition 
<br/>
<p style="text-align: justify;">
Up to now, I see convolution operations as a way to extract information from a single object observed. I still have this strong example that resonates with me.
Let's say we are a chemist and we want to study the behaviors of a particular virus put on several kinds of environments. We try first to let the virus in a sugar-free environment, <mark>then observe and take notes of what is happening then we change</mark>, and so on until we have exhausted all the possibilities of our imaginations.
</p>

<br/>
<p style="text-align: justify;">
Then all those notes we have collected become a set of information or features that correspond to that virus when being exposed to a certain kind of environment. 
This is a very simple example but I feel it gives me a better introduction or intuition to convolution operations.
</p>

<br/>
<p style="text-align: justify;">
The analogy is simple. The different environments represent in technical terms, the filters, or the kernels. The virus itself could be represented as the original 
object we want to extract its associated features or behaviors (sometimes it is a picture, a text, a signal, etc...).
</p>

<br/>
<p style="text-align: justify;">
The thing is that we are observing the behavior but we are not labeling it. We just know that in this environment, the virus has behaved that way. But we don't know why. And it is okay because we just want to observe the behaviors not to know why at this step. We just want to collect the <strong>Hows</strong>? (how the virus behaves) rather than <strong>Why</strong> is it so...
</p>


<br/>
<p style="text-align: justify;">
So in simple terms, we can see that if we know how to select <mark>the correct sets of environments</mark>, we can learn so interesting behaviors concerning the virus. This is what it is all about when thinking of convolution operations or at least for this introduction about it. We don't want to directly and manually extract those features like it could be done by a chemist, rather, we want to make it automatic but at the same time, we want to know the most important environments that trigger certain behaviors because not all environments will give us good information in the same way not all the kernels or filters will extract important features. 
</p>

<br/><br/>
## Objectives 
<br/>

<p style="text-align: justify;">
For this first experiment about convolution operations, I just want to implement it from scratch in C++ and get the intuition behind it. Because first, I want it to stay in this environment for my experiments. It gives a deeper control over my thinking processes but also be <mark>a bit closer</mark> to the hardware logic.
This first experiment is to understand how a simple convolution can be implemented in C++. And focusing on the logic implementation. Then, the following experiments 
will be about studying more in deep the convolution operations and associated ones.
</p>

<br/><br/>
## References
<br/>

<p style="text-align: justify;">
To refresh my understanding of Convolution operations specifically in AI, I had to go over two articles. One is a Github repo and the one is an article well written by Himanshu Dubey I suggest reading for a better overview of how convolution ops are implemented in a CNN model. Here are the two references:
</p>
<br/>

- [Intuition of Convolution in Python](https://github.com/detkov/Convolution-From-Scratch)
- [CNN from scratch with pure Math intuition](https://lunar-joke-35b.notion.site/CNN-from-Scratch-with-pure-Mathematical-Intuition-a201ef0ca1314058a1707a3ae260981e) (also Python)

<br/>
<p style="text-align: justify;">
I recommend these resources for a broader understanding of how convolution operations are implemented in CNN models since they have great illustrations.
</p>

<br/><br/>
## Experiment 
<br/>

<p style="text-align: justify;">
In the first step, I had to outline how it could be implemented and what could be the general steps to go through in order to perform a simple 2D convolution.  
</p>
<br/>
So what is the problem (technically speaking)?
<br/>

<p style="text-align: justify;">
We have now an object which is here represented as a matrix (2 dimensions). Not only that, we have one separate environment we want to try the object on which is here in our case a filter or a kernel which is also of a 2-dimensional size. But here is the catch, for a simple implementation, <mark>the kernel size must be equal or less than the size of the object</mark> (original matrix).
</p>

<br/>
<p style="text-align: justify;">
Yes, it does not make sense with the analogy where we talk about environments because in that case, the kernel has to be bigger right? but we want to have an environment that makes sense for us to observe the virus. For example, We know that the virus directly dies after a few seconds in an environment that has a temperature higher than 200 degrees Celcius. This is beyond the limits of the virus so why should we take into account such environments with <strong>higher</strong> temperatures? So it makes sense, for now, to not take a kernel bigger than the object size (original matrix).
</p>
<br/><br/>

### Plan of Experiment 
<br/>

<p style="text-align: justify;">
The first step, in this experiment was to identify the most important operation or core operation in the 2D convolution operation. What I got was that the most important was to implement the element-wise multiplication that happens during the 2D convolution operation. I will put the math formula later on but here is the plan I designed:
</p>

<br/>
- Build a function that takes two matrices of the same size and computes their resulting matrix from an element-wise multiplication operation; 
- Find a way to extract sub-matrices from top-left to right in a descending order(top to bottom) in the original matrix (bigger matrix) which has the same size as the kernel;
- Use the function built to compute the resulting matrix in an element-wise fashion; 
- Take the resulting matrix and sum all the elements inside it. Save the value in a secure place where it will serve as an element of the final convolution matrix;
- Repeat from step 3 until we have exhausted all the possible positions given by the matrix size, the kernel, and the move set to 1 from left to right (This move is called stride).


<br/>
<p style="text-align: justify;">
The motive behind the first step is that it makes it much easier to solve the problem by identifying <mark>the core operation or operations</mark> and then link all together.
As we can understand this problem, the function built on the first step will serve recursively until we reach the last position possible by the kernel inside the original matrix.
</p>

<br/>
### Step 1: Build the element-wise function multiplicator 
<br/>
### Problem definition:
<br/>

So what is the problem here? <br/> <br/>

<p style="text-align: justify;">
Given two matrices of the same size, return a matrix that is the product of an element-wise multiplication of the two. 
</p>

<div style="text-align: center;">
$$
C[i, j] = A[i, j] \times B[i, j]
$$
$$ i = 1,..., m & j=1,...,n$$

</div>
<br/>
<div style="text-align:center;">

<figure style="text-align: center;">
    <img src="https://raw.githubusercontent.com/Anvi98/anvi98.github.io/master/assets/images/khan_academy_matrix_product.gif" alt="element-wise multiplication illustration" width="300"/>
    <br />
    <figcaption>Fig.1: Element-wise multiplication (Khan academy).
    </figcaption>
</figure>
</div> 

<br/>
### Code it now: 
<br/>

<p style="text-align: justify;">
The quality of this step depends on experience with the language and mine is not the top one. I actually went a bit further and computed the result value on step 4 (mentioned earlier) and returned it through the function. This is one way to implement it: 
</p>

<br/>
<p style="text-align: justify;">
I kept the documentation so that it will be easier to remember the logic.
</p>

```cpp
/**
 * @brief Performs element-wise multiplication between a matrix and a kernel.
 * 
 * @tparam M Number of rows in the kernel.
 * @tparam N Number of columns in the kernel.
 * @param matrix The matrix to be multiplied.
 * @param kernel The kernel to apply on the matrix.
 * @return std::tuple<int, std::vector<std::vector<int>>> A tuple containing the sum of all elements 
 * and the resulting matrix after element-wise multiplication.
 */
template <size_t M, size_t N>
std::tuple<int, std::vector<std::vector<int>>>
element_wise_matmul(
    const std::vector<std::vector<int>>& matrix, 
    const std::array<std::array<int, M>, N>& kernel
    ){

    size_t numCol_matrix = matrix.size(); 
    size_t numRow_matrix = matrix[0].size(); 
    size_t numCol_kernel = M; 
    size_t numRow_kernel = N;

    std::vector<std::vector<int>> res_matrix(numCol_kernel, std::vector<int>(numRow_kernel, 0));
    int sum_elements = 0;
 
  for(size_t i = 0; i < numRow_kernel; i ++){
      for(size_t j = 0; j < numCol_kernel; j ++){
        res_matrix[i][j] = kernel[i][j] * matrix[i][j]; // here is the element-wise multiplication 
        sum_elements += res_matrix[i][j]; // Here is saving incrementally of each result from the multiplication.
      }
    }
 
  return std::make_tuple(sum_elements, res_matrix); // I have decided to return the res_matrix for debugging purposes.
}

```
<br/><br/>
### Explanation of Code 
<br/> 

<p style="text-align: justify;">
The logic in my mind while coding the function was to take two matrices (an original matrix and a supposed kernel) of the same dimensions. 

Since the experiment was meant to be intuitive and introductory, I hard-coded the matrices and defined them as vectors and arrays of known size respectively. Then I made use of a nested for loop to represent the logic of the element-wise multiplication. 
</p>

<br/>
<p style="text-align: justify;">
The nested for loop accesses each element of both matrices and multiplies them according to the formula of element-wise multiplication.</p>
<br/>



<br/><br/>
### Step 2: Find a way to extract the matrix from the Original matrix 
<br/>

<p style="text-align: justify;">
Now that I can compute the element-wise multiplication if I have the correct input matrices, the problem is how to get those inputs from the given matrices I have. For the kernel, it is already given because the current experiment is simple. So the whole problem relies on getting the sub-matrices from the original matrix.
This part is the most <mark>tricky and important</mark> after the function is built in the first step:
</p>

<br/>
```cpp
... 

// Get some info about the max move to perform 
int max_move_right = ((numCol_m - numCol_kernel)/stride) +1 ; 
  int max_move_down = ((numRow_m - numRow_kernel)/stride) + 1;
  int start_idx_col = 0, start_idx_row = 0 ;


  std::vector<std::vector<int>> conv_result_matrix(max_move_down, std::vector<int>(max_move_right, 0));
  
  // Use the info to traverse the matrix and extract sub-matrix
  for(int i=0; i< max_move_right * max_move_down; i ++){
    // Extracting sub matrix from original one
    std::vector<std::vector<int>> tmp_sub_matrix(numRow_kernel, std::vector<int>(numCol_kernel));
    for(size_t j = 0 + start_idx_row ; j <numCol_kernel + start_idx_row; j ++){
      for(size_t k = 0 + start_idx_col ; k<numRow_kernel + start_idx_col; k++){
        tmp_sub_matrix[j - start_idx_row][k - start_idx_col] = matrix[j][k];
      }
    }

    ... // (There is a chunk of code missing here)

    if(start_idx_col == max_move_right - 1){
      start_idx_col = 0;
      start_idx_row ++;
    }

    else {
      start_idx_col ++;
    }

}  

```
<br/><br/>
### Explanation of Code 
<br/>

<p style="text-align: justify;">
Above is the chunk of code I implemented for extracting in an <mark>(in-line fashion)</mark> the submatrix given that I have the maximum number of moves to perform from top-left to bottom-right. The most important part to remember in this chunk is the definition of the temporary vector that stores the submatrix and after each iteration is initialized and modified. 
</p>

<br/>
- The variables start_idx_col and start_idx_row are used here based on the logic I came up with during the coding phase. They serve as cursors and indicators to know what which moment the algorithm has to go down or continue sliding at the right side; 

- The main loop will iterate max_move_right * max_move_down which is the final dimension of the matrix resulting from the convolution operation; 

- The subtraction I performed was the way I came up with to make sure the algorithm is not accessing the submatrix with an index out of boundaries since the size of the submatrix is already defined being the size of the kernel. 

<br/><br/>
### Step 3: Convolution Calculation 
<br/>

<p style="text-align: justify;">
I have put previously in the code section that there is a missing code. Here is the code. It performs the full element-wise multiplication after extracting the current sub-matrix at the position i. Recall that the previous code was to design the function logic and here I am calling it to perform the operation: 
</p>

<br/>
```cpp
// Perform element-wise ops 
auto [sum_res, sub_res_m] = element_wise_matmul(tmp_sub_matrix, kernel); // call of the element-wise_matmul
conv_result_matrix[start_idx_row][start_idx_col] = sum_res;

```
<br/><br/>
### Full 2D convolution operation function
<br/>

Now, I can better understand the full logic of the 2D convolution operation through the code:
<br/>
```cpp
/**
 * @brief Applies a 2D convolution operation on an input matrix using a given kernel.
 * 
 * @tparam M Number of columns in the input matrix.
 * @tparam N Number of rows in the input matrix.
 * @tparam O Number of columns in the kernel.
 * @tparam P Number of rows in the kernel.
 * @param matrix The input matrix to apply the convolution to.
 * @param kernel The kernel used for the convolution.
 * @return std::vector<std::vector<int>> The result of the convolution operation.
 * @throws std::invalid_argument If the kernel dimensions exceed the matrix dimensions.
 */
template <size_t M, size_t N, size_t O, size_t P> 
std::vector<std::vector<int>> conv2D(std::array<std::array<int, M>, N>& matrix, std::array<std::array<int, O>, P>& kernel){
  // find the max_moves for rows and columns
  int numCol_m = M;
  int numRow_m = N;
  int numCol_kernel = O;
  int numRow_kernel = P;
  int stride = 1;

  int max_move_right = ((numCol_m - numCol_kernel)/stride) +1 ; 
  int max_move_down = ((numRow_m - numRow_kernel)/stride) + 1;
  int start_idx_col = 0, start_idx_row = 0 ;


  std::vector<std::vector<int>> conv_result_matrix(max_move_down, std::vector<int>(max_move_right, 0));

  for(int i=0; i< max_move_right * max_move_down; i ++){
    std::vector<std::vector<int>> tmp_sub_matrix(numRow_kernel, std::vector<int>(numCol_kernel));
    for(size_t j = 0 + start_idx_row ; j <numCol_kernel + start_idx_row; j ++){
      for(size_t k = 0 + start_idx_col ; k<numRow_kernel + start_idx_col; k++){
        tmp_sub_matrix[j - start_idx_row][k - start_idx_col] = matrix[j][k];
      }
    }
    // Perform element-wise ops 
    auto [sum_res, sub_res_m] = element_wise_matmul(tmp_sub_matrix, kernel);
    conv_result_matrix[start_idx_row][start_idx_col] = sum_res;

    if(start_idx_col == max_move_right - 1){
      start_idx_col = 0;
      start_idx_row ++;
    }

    else {
      start_idx_col ++;
    }
  
  }
  return conv_result_matrix;
}
```
<br/><br/>

### Explanation of the code
<br/>
The function built returns a matrix that results from a 2D convolution operation (a simple one).

<br/><br/>
### The main logic: Combine all pieces of code
<br/>
Now that I have been able to build each core operation I can wrap them into a main function that executes them all together:
<br/>

```cpp
int main(void){
  
  // get sizes
  const auto [numrow_m, numcol_m, numrow_kernel, numcol_kernel] = get_matrix_sizes(matrix_1, kernel);

  //check matrix and kernel dimensions
  bool is_same_size = true;
  if(numcol_kernel*numrow_kernel > numcol_m*numrow_m){
    throw std::invalid_argument("kernel dimensions goes beyond matrix dimensions.");
    is_same_size = false;
    return -1;
  }
  
  //apply convolution
  auto conv_result_matrix = conv2d(matrix_1, kernel);
  
  // display results matrix after convolution
  std::cout<<"-----------res conv --------------\n";
  for (size_t i = 0; i < conv_result_matrix.size(); ++i) {
    for (size_t j = 0; j < conv_result_matrix[0].size(); ++j) {
      std::cout<<conv_result_matrix[i][j]<<" ";
    }
    std::cout<<'\n';
  }

  return 0;
}

```
<br/><br/>
### Explanation of the piece of Code 
<br/>

<p style="text-align: justify;">
First and foremost, I needed to get the sizes of the concerned matrices (kernel and original matrix). then I needed to make sure of the match between their sizes 
due to the constraint of the element-wise multiplication principle. When everything is good, I call the conv2D function on the kernel and matrix. 
Finally, I output the resulting matrix. This is the end of the implementation but it is just the beginning of a bigger experiment as you can see in the second reference I mentioned at the beginning. 
</p>

<br/><br/>

## Major challenges
<br/>

The major challenge I have to go through is to understand practically the relationships between the 2D convolution logic I was implementing and selecting the 
correct data type. Either a C-like array or a vector. Not only that, I had some few times debugging <mark>which 'i' or 'j' in loops represent the columns or rows which was resulting in some out of bounds access errors</mark>.

<br/><br/>

## Limits 
<br/>

This first implementation is extremely limited and for now, I can cite:
- The code does not take into account floating points
- The code is not fully optimized
- No padding considerations 
- etc...

<br/>
<p style="text-align: justify;">
The next experiments concerning convolutions will be more deeper and will tackle several aspects of it and the limits mentioned will be fixed. 
</p>

<br/><br/>
## Where to get the full code?
<br/>
The full code as of now, can be found in the GitHub repository:
<br/><br/>

**[Full code](https://github.com/Anvi98/convolution)** (It has all the .cpp, .tpp and .hpp files with comments).
<br/><br/>
## Takeaway 
<br/>

<p style="text-align: justify;">
Definitely, this first experiment targets the understanding of convolution operations from an intuitive approach and also attempts to build the operation from scratch using a language like C++ which I have some preference for. So except that there is no big takeaway. But I believe the next experiments will give me some insights on performances (on memories, spaces, power, etc...), but also alternatives.
</p>
<br/>
<br/>
