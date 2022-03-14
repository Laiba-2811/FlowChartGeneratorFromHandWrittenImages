# FlowChartGeneratorFromHandWrittenImages</br>
1 Introduction</br>
Often when we are prototyping new ideas, a flowchart will be an ideal way to explicit our thoughts.
However, it could be super time consuming to draw up a well-organized one onto our documentation
files or presentation. In that sense, it would be really convenient if we can automatically generate the
flowchart template with proper order informed from hand drawing chart.The system can be applied
in many settings from discussion and notes in daily use to formal meetings in company or education
institution.</br>
3 Methodology</br>
To make the objective achievable, several assumptions are made, like,Each components in the handwritten flowchart should be closed graph,The arrows in the curve must be straight,The shape that can
be recognized is restricted to rectangle, arrow, diamond and circle and No intersections among arrows.The first step is to input a flowchart.The input image usually has three channels, RGB. Then we
converted the input flowchart to a gray-scale image.After converting the image into gray-scale, we
employ an Gaussian filter to remove the salt-and-pepper noise caused by camera. The improvements
can be observed explicitly after an adaptivethreshold binarization operation. The filter size for this binarization is tuned carefully, because it is pretty sensitive to the change of contrast and luminance.
Now, we have an image with black front-ground flow chart shapes and white background.The final
operation in this step is a bit-wise inversion, to swap the front-ground and background colors. Then
we performed de-noising.The ”noise” in this step is the small areas that inappropriately generated
by the binarization operation or caused by stains on the paper .Gaussian filter doesn’t work again.
Here, we remove all these small areas in another way. First, find all contours in the white foreground
shapes. Second, fill black color into the contours with area smaller than the threshold we set. This
procedure effectively eliminates all the irrelevant small areas and leaves the flowchart in the background.Then edges will be analyzed by Hough transform to extract their angles. A histogram is
generated then according to these angles.After all the components are disconnected after decomposition step, we found and labeled the connected ones to determine the regions of each shape.Then
connection relationship has been built.The goal of this step is to determine the direction of arrows.
Since the width, height and the upper left point of the boundary box is known, the center of the
box can also be computed. By comparing the relative location of the center and the centroid of the
shape, the corner that is closet to the centroid can be found. Based on the assumption that the arrows
are straight, the closet corner can approximate the head of the arrow, and the diagonal corner would
represent the tail of the arrow.After this, characterization has been performed.</br>
4 Experiments and Results</br>
4.1 Qualitative evaluation</br>
For the smoothing of an input image, we have used gaussian smooth and fastnlmeansdenoising. It
Performs image denoising using Non-local Means Denoising algorithm with several computational
optimizations. We have used erosion and dilation method to get the best edges or shapes.We applied
canny edge detection.Canny edge detection is a technique to extract useful structural information
from different vision objects and dramatically reduce the amount of data to be processed.We applied
hough transform.The Hough transform is a feature extraction technique used in image analysis,
computer vision, and digital image processing. The purpose of the technique is to find imperfect
instances of objects within a certain class of shapes by a voting procedure.
