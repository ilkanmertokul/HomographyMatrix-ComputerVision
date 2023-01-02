# HomographyMatrix-ComputerVision
In this task, i capture image of a target soccer field on paper. My program will then estimate a homography that transforms this image to model soccer field.

Homework file’s ipynb file has 2 parts: first part defines functions, second part
is what we run.
# HOW TO USE
User should choose corners in “counter clockvise” order. Because warpped
photo’s corners are ordered like this:

![Ekran görüntüsü_20230102_170620](https://user-images.githubusercontent.com/61903795/210242062-18331ebf-c823-4d54-afa1-30accdc70dc1.png)

So user must have set their order according to this to get working homography.<br />
Output photo will be in 600x450. There will be two versions of photo.<br /><br />
1- OpenCV2 calculations of homography matrix<br />
2- Find_homography(…) calculation of homography matrix.<br /><br />
And output should look like this:<br />
![Ekran görüntüsü_20230102_170658](https://user-images.githubusercontent.com/61903795/210242104-ef7dbf19-1546-4273-8afa-b263e414e475.png)
If cannot read, red box’ window is opencv homography, orange box’ window is
computed homography.<br />

# Calculating Homography
I did not derive and found any of these homographies myself. I used internet to
get help and used singular value decomposition (SVD) to find homography with
the help of NUMPY library from python.<br />
https://ros-developer.com/2017/12/26/finding-homography-matrix-usingsingular-value-decomposition-and-ransac-in-opencv-and-matlab/<br />
https://www.youtube.com/watch?v=MlaIWymLCD8&t=1120s<br />
https://math.stackexchange.com/questions/494238/how-to-computehomography-matrix-h-from-corresponding-points-2d-2d-planar-homog<br />
These links helped me to build the function.<br />
First of all, i get this matrix A.<br />

![Ekran görüntüsü_20230102_170730](https://user-images.githubusercontent.com/61903795/210242168-9e70fccf-77e3-404f-9402-7a0b6bbfe304.png)

After that, use SVD to get U , Σ and V. V’s last column gets reshaped to give us
Homography matrix.<br />
![Ekran görüntüsü_20230102_170748](https://user-images.githubusercontent.com/61903795/210242205-4327e3e5-aa65-4730-a590-9a75511c8998.png)

Results are not exactly the same, but they give really close results.<br />
Other results as screenshots:
![Ekran görüntüsü_20230102_170809](https://user-images.githubusercontent.com/61903795/210242256-9752d9d3-5792-4093-adf8-cc4d5094357d.png)
![Ekran görüntüsü_20230102_170815](https://user-images.githubusercontent.com/61903795/210242264-ca538ec0-7eb2-4b1a-890d-22036ec75bdd.png)

