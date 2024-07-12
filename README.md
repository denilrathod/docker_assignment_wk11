Git hub link :- https://github.com/denilrathod/docker_assignment_wk11
Docker Repo Link: https://hub.docker.com/r/prabhmeetsingh44412/goapi/tags
Docker Link to Pull the image: docker pull prabhmeetsingh44412/goapi:01


Step 1 : Set Up Development Environment
Install Go:
According to  the instructions on the Go installation page for  downloading  and install.  Go on  system.
Install Git:
According to  the instructions on the Git installation page for  downloading  and install Git on system.
Install Docker:
 According to  the instructions on the Docker installation page to download and install Docker on system.
Step 2:  Create the API Server
1.	Initialize a New Go Module:
                Open your terminal and navigate to your project directory.
                Run the following command to initialize a new Go module:
2.	Create the main.go File using  the Required Endpoints:
                 In your project directory, create a file named as “main.go” after that add the following             code:
               package main

        2.1   import (
	"fmt"
	"log"
	"net/http"
                 )

                      'package main': the main package is entry of the go application 

                'import ("fmt" "log" "net/http")':import these packages. fmt for formatting, log for logging,           net/http for HTTP client and server implementations. 

2.2.	func homeHandler(w http.ResponseWriter, r *http.Request) {
	if r.URL.Path != "/" {
		http.NotFound(w, r)
	}
	fmt.Fprintln(w, "Welcome to the Go API Server!")
                } 
               homeHandler: this function handles requests 
               http.ResponseWriter: write responses 
              http.Request: request information 
                if request path is other than "/" it shows 404 error otherwise "welocme to the GO API server" 

2.3.	func aboutHandler(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "This is the About page.")
                    } 
                   this handler is for about page 


2.4.	func main() {
	mux := http.NewServeMux()
	mux.HandleFunc("/", homeHandler)
	mux.HandleFunc("/about", aboutHandler)

	log.Println("Starting server on :3003")
	err := http.ListenAndServe(":3003", mux)
	if err != nil {
		log.Fatalf("Error starting server: %s\n", err)
	}
               } 

                     main: entry point 
                    NewServerMux(): create new HTTP request 
                      mux.HandleFunc("/", homeHandler): register homelander function to handle request to "/" route 
                      mux.HandleFunc("/about", aboutHandler): register the aboutHandler fucntion to handle            request "/about" route 
                    log.Println("Starting server on :3003"): logs message to start server onport 3003 
                     http.ListenAndServe(":3003", mux): starts the HTTP server on 3003

step3: Version Control with Git
1.	Initialize a New Git Repository:   In your project directory, run the following command to initialize a new Git repository
                  git init
2.	Add and Commit the Code:
Git add .
Git commit -m “Initial commit”
3.	Push the Code to GitHub:
                 git remote add origin https://github.com/danilrathod/docker_assignment_wk11.git
                  git push -u origin  main

Step 4: Create a Dockerfile
1.	WORKDIR /app: This sets the working directory for the Docker container to /app. All commands will  run in this directory in sequential manner. 
2.	COPY . . : This copies the entire content from  current directory (where the Dockerfile is located) to the working directory /app inside  the Docker container. This includes source code and other necessary files as well.
3.	RUN “CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main” 
4.	EXPOSE 3003: This informs Docker that the container listens on port 3001 at runtime. It does not actually publish the port; it’s a way to document the intended port.
5.	CMD ["./main"]: This specifies the command to run when the container starts. It runs the compiled Go application named main.

Step 5: Build and Push Docker Image
1.	Build the Docker Image:
                          docker build -t  goapi:01 .
2.	Log in to Docker Hub:
3.	Push the Docker Image to Docker Hub:
  docker push prabhmeet44412/goapi:01






