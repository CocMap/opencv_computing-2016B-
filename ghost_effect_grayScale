// Ghost effect video
#include <cv.h>   // headers
#include <highgui.h>
#include <opencv2/core/core.hpp>
#include <opencv2/highgui/highgui.hpp>
#include <opencv2/imgproc/imgproc.hpp>
#include <opencv2/opencv.hpp>
#include <opencv2/videoio/videoio.hpp>

using namespace cv;

int main(  int argc, char** argv ) {
	int frameCount;
	Mat frame;
	Mat currentFrame;
	Mat preFrame;
	Mat grayFrame;
	Mat grayDiff;
	Mat frameDiff;
	int motion = 0;

	VideoCapture cap(0);				//open default camera
	if(!cap.isOpened()){
		return -1;
	}
	cap >> frame;

	namedWindow("Ghost effect",CV_WINDOW_AUTOSIZE);

	for (; ; frameCount++){
						//take the original one, set as previousFrame, take effect
		frame.copyTo(preFrame);

		cap >> currentFrame;			//take the current frame, compare with the previousFrane
		absdiff(currentFrame,preFrame,frameDiff);
		cvtColor(frameDiff,grayDiff,CV_RGB2GRAY);

		motion = motion + grayDiff.at<uchar>(0.0);

		imshow("Ghost effect",grayDiff);

		if(waitKey(20) >= 0) break;


	}
    return 0;

}




