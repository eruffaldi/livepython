# livepython
Live Python editing for testing OpenCV algorithms, when Jupyter is not enough

Every code change in the editor is sent to the Python server executed live INSIDE the OpenCV loop. The OpenCV loop is executed with 1ms wait

Client: CodeMirror editor with two panels (editor+errors)
Server: Tornado Websocket 

# Running

Satisfy Python Dependencies:	

	pip install -r requirements.txt

Run: 
	
	python livecv.py

Open Web browser at: localhost:8000

# Python Environment
	
The environment is a functon that can be escaped by return (closes the program):

- cv2,np modules
- data, a dictionary for easing the definition and storage of global variables 
- imshow(image), for showing in the "live" window

In addition OpenCV is inited with a window named "live"

# Example
Simple example

	lastimg = data.get("img")
	if lastimg is None:
	  lastimg = cv2.imread("example.jpg",cv2.IMREAD_COLOR)
	  data["img"] = lastimg
	nextimg = lastimg*2

	imshow(nextimg)
	cv2.resizeWindow("live",640,400)

# Future

- HTML5 widgets (trackbar...)
- Profiling information
- Auto open the browser
- Improved API for easing plotting 
- Using Queue for the OpenCV loop instead of the wait
- Python live video and repeat execution for every frame