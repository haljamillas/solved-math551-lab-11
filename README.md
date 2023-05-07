Download Link: https://assignmentchef.com/product/solved-math551-lab-11
<br>
<strong>Goal: </strong>In this lab, you will learn to use the singular value decomposition for image compression.

<strong>Getting started: </strong>You will need to download the file TarantulaNebula.png and put it in your working directory.

<strong>What you have to submit: </strong>The file m551lab11.m, which you will create during the lab session.

<strong>Reminders About the Grading Software</strong>

Remember, the labs are graded with the help of software tools. If you do not follow the instructions, you will lose points. If the instructions ask you to assign a value to a variable, you must <strong>use the variable name given in the instructions</strong>. If the instructions ask you to make a variable named x1 and instead you make a variable named x or X or X1 or any name other than x1, the grading software will not find your variable and you <em>will </em>lose points. Required variables are listed in the lab instructions in a gray box like this:

<h1>Variables: x1, A, q</h1>

At times you will also be asked to answer questions in a comment in your M-file. You must <strong>format your text answers correctly</strong>. Questions that you must answer are shown in gray boxes in the lab. For example, if you see the instruction

Q7: What does the Matlab command lu do? your file must contain a line similar to the following somewhere

% Q7: It computes the LU decomposition of a matrix.

The important points about the formatting are

<ul>

 <li>The answer is on a single line.</li>

 <li>The first characters on the line is the comment character %.</li>

 <li>The answer is labeled in the form Q<em>n</em>:, where <em>n </em>stands for the question number from the gray box.</li>

</ul>

If you do not format your answers correctly, the grading software will not find them and you <em>will </em>lose points.

<strong>Tasks</strong>

<ol>

 <li>Open an M-file called m and add the following commands</li>

</ol>

t=linspace(0,2*pi,100); X=[cos(t);sin(t)]; figure(1);

plot(X(1,:),X(2,:),’b’); axis equal

this will create a 2 × 100 matrix <strong>X </strong>= [<strong>x</strong><sub>1 </sub><strong>x</strong><sub>2 </sub>··· <strong>x</strong><sub>100</sub>] whose columns are unit vectors pointing in various directions. The plot will show a blue circle corresponding to the endpoints of these vectors. Variables: X

<ol start="2">

 <li>Now in the M-file, define a variable A holding the matrix</li>

</ol>

<strong>A </strong>

and a variable AX holding the product A*X. Note that this product equals

<strong>AX </strong>= [<strong>Ax</strong><sub>1 </sub><strong>Ax</strong><sub>2 </sub>··· <strong>Ax</strong><sub>100</sub>]<em>,</em>

so the columns of AX show where the matrix <strong>A </strong>maps each of the columns of <strong>X</strong>. Add the following lines to your M-file after the definition of AX.

figure(2); plot(AX(1,:),AX(2,:),’b’); axis equal

Now when you run the M-file you should see a blue circle in Figure 1 and a blue ellipse in Figure 2. This shows that <strong>A </strong>maps vectors that end on the unit circle to vectors ending on an ellipse. Variables: A, AX

<ol start="3">

 <li>Add the following line to your M-file and re-run the file.</li>

</ol>

[U,S,V] = svd(A)

Your output should look like this

U =

<table width="126">

 <tbody>

  <tr>

   <td width="75">-0.9571</td>

   <td width="50">0.2898</td>

  </tr>

  <tr>

   <td width="75">0.2898S =</td>

   <td width="50">0.9571</td>

  </tr>

  <tr>

   <td width="75">2.3028</td>

   <td width="50">0</td>

  </tr>

  <tr>

   <td width="75">0V =</td>

   <td width="50">1.3028</td>

  </tr>

  <tr>

   <td width="75">-0.9571</td>

   <td width="50">-0.2898</td>

  </tr>

  <tr>

   <td width="75">-0.2898</td>

   <td width="50">0.9571</td>

  </tr>

 </tbody>

</table>

The function svd computes the singular value decomposition of <strong>A</strong>:

<strong>A </strong>= <strong>USV</strong><em><sup>T</sup></em>

where <strong>U </strong>= [<strong>u</strong><sub>1 </sub><strong>u</strong><sub>2</sub>] and <strong>V </strong>= [<strong>v</strong><sub>1 </sub><strong>v</strong><sub>2</sub>] are orthogonal matrices and

<strong>S </strong>

is a non-negative diagonal matrix. Moreover

[<strong>Av</strong><sub>1 </sub><strong>Av</strong><sub>2</sub>] = <strong>AV </strong>= <strong>USV</strong><em><sup>T</sup></em><strong>V </strong>= <strong>US </strong> <em>,</em>

showing that

<strong>Av</strong><sub>1 </sub>= <em>σ</em><sub>1</sub><strong>u</strong><sub>1                      </sub>and           <strong>Av</strong><sub>2 </sub>= <em>σ</em><sub>2</sub><strong>v</strong><sub>2</sub><em>.</em>

You can check this fact in the command window as follows.

&gt;&gt; A – U*S*V’ ans =

1.0e-15 *

0.8882             0.4441

-0.4441             0.2220

&gt;&gt; U’*U ans =

1.0000                         0

<ul>

 <li>0000</li>

</ul>

&gt;&gt; V’*V ans =

<ul>

 <li>0</li>

</ul>

0             1

<h1>Variables: U, S, V</h1>

<ol start="4">

 <li>Plot the columns of <strong>V </strong>on Figure 1 by adding the following to your M-file.</li>

</ol>

figure(1); hold on; quiver(0,0,V(1,1),V(2,1),0,’r’); quiver(0,0,V(1,2),V(2,2),0,’g’); hold off;

The vector corresponding to the first column will be plotted in red and the second column in green.

<ol start="5">

 <li>Plot the columns of <strong>US </strong>on Figure 2 by adding the following to your M-file.</li>

</ol>

figure(2); hold on; quiver(0,0,S(1,1)*U(1,1),S(1,1)*U(2,1),0,’r’); quiver(0,0,S(2,2)*U(1,2),S(2,2)*U(2,2),0,’g’); hold off;

The vector corresponding to the first column will be plotted in red and the second column in green.

<ol start="6">

 <li>Now we’ll work on a bigger matrix. Add the following commands to your M-file and run it. (If you want, you can create a new cell by entering two percent signs (%%) at the beginning of a line and just run the cell from now on.)</li>

</ol>

%% (start a new cell)

Img = double(imread(’TarantulaNebula.png’)); figure(3); image(Img); colormap(gray(256));

This code loads an image as a real matrix and displays it on the screen. Each entry in the matrix corresponds to a pixel on the screen and takes a value somewhere between 0 (black) and 255 (white).

Variables: Img

<ol start="7">

 <li>Perform the singular value decomposition of Img, save the output in matrices UImg, SImg, and VImg.</li>

</ol>

<h1>Variables: UImg, SImg, VImg</h1>

<ol start="8">

 <li>Add the following code and run the M-file.</li>

</ol>

figure(4); semilogy(diag(SImg));

This shows the singular values (the diagonal entries of the <strong>S </strong>matrix) for our image matrix (the scale of the <em>y </em>axis is logarithmic). Notice that the diagonal entries of <strong>S </strong>are ordered so that <em>σ</em><sub>1 </sub>≥ <em>σ</em><sub>2 </sub>≥ <em>σ</em><sub>3 </sub>≥ ···. One way of writing the SVD is

<strong>A </strong>

where <em>r </em>is the rank of <strong>A </strong>and <strong>u</strong><em><sub>i </sub></em>and <strong>v</strong><em><sub>i </sub></em>are the <em>i</em>th columns of <strong>U </strong>and <strong>V </strong>respectively.

If for some <em>k &lt; r</em>, <em>σ<sub>k</sub></em><sub>+1 </sub>is very small compared to <em>σ</em><sub>1</sub>, we should expect

<strong>A</strong>

to be a good approximation of <strong>A</strong>. (This is called a truncated SVD.) This idea can be used for image compression as follows. Instead of storing the whole <em>m </em>× <em>n </em>matrix <strong>A</strong>, we instead store the <em>m </em>× <em>k </em>and <em>n </em>× <em>k </em>matrices

<strong>C </strong>= [<strong>u</strong><sub>1 </sub><strong>u</strong><sub>2 </sub>··· <strong>u</strong><em><sub>k</sub></em>]            and             <strong>D </strong>= [<em>σ</em><sub>1</sub><strong>v</strong><sub>1 </sub><em>σ</em><sub>2</sub><strong>v</strong><sub>2 </sub>··· <em>σ<sub>k</sub></em><strong>v</strong><em><sub>k</sub></em>]<em>.</em>

If <em>k</em>(<em>m </em>+ <em>n</em>) is much smaller than <em>mn</em>, then storing <strong>C </strong>and <strong>D </strong>will take much less space than storing <strong>A</strong>. Moreover, if we wish to display the image, we can reconstruct <strong>A </strong>(approximately) as <strong>A </strong>≈ <strong>CD</strong><em><sup>T</sup></em>.

<ol start="9">

 <li>Add the following code to your M-file. %% (start a new cell) k = 10;</li>

</ol>

% compressed image

<ul>

 <li>= UImg(:,1:k);</li>

 <li>= VImg(:,1:k)*SImg(1:k,1:k);</li>

</ul>

% compression percentage pct = 1 – (numel(C)+numel(D))/numel(Img);

figure(5); image(C*D’); colormap(gray(256)); title( sprintf( ’%.2f%% compression’, 100*pct ) );

figure(6); image(Img); colormap(gray(256)); title( ’Original’ );

This code compresses the image as described above using <em>k </em>= 10 singular values, then displays the reconstructed image along with the original. It also shows the percent decrease in storage size required for the compressed image. Try several values of <em>k </em>to see how the quality and compression percentage vary with <em>k</em>. Set k so that the compression percentage is 80<em>.</em>23% before turning in your M-file.

<h1>Variables: k, C, D</h1>