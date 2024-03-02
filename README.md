Overview
===

This is a small project developed for the final project of EEP520 at the University of Washington. It contains a maze built with the Enviro environment and a simulated robot that uses Enviro and Elma to navigate through the constructed labyrinth. The robot uses a wall tracking routine to follow the right wall to the end of the maze. This method allows navigation through complex maze with dead ends. When the robot has completed the maze, a message is displayed in the terminal and the robot is reset.

Key challenges
===
Challenge 1:
I originally intended to configure the Enviro environment using Git Bash, but encountered an error: "the input device is not a TTY. If you are using mintty, try prefixing the command with 'winpty'." Eventually, I resolved it by setting up the winpty environment on my Windows system. Additionally, I faced other setup issues related to the Windows system. I found solutions online and discussed them with my classmates, successfully resolving all of them.

Challenge 2:
I wanted the robot to be able to navigate through any given maze without a given path. This led to investigations into the proposed methods, including the method of demolition. Somewhat unintuitively, a robot that follows a single wall long enough always finds the end of the labyrinth. This proved to be a reasonably accessible and effective method.

Challenge 3:
Initially friction between the robot and the wall eventually caused the robot to get stuck. To simplify the process and avoid failures, friction between the robot and wall was disabled.

Challenge 4:
Determine the end of the maze. First, I tried to use a block at the end of the maze to detect a collision with the robot and trigger a reset of the robot. Unfortunately, this caused strange errors and occasional "segmentation errors", and I overcame this by determining when the robot reached the upper right corner of the maze based on the robot's position.

Install and run the code:
===
You can also build the docker environment, described in env/Dockerfile, yourself, with the following commands. These commands were tested using git bash within VS Code:

    git clone https://github.com/jeffiskater/final_project.git
    docker run -p80:80 -p8765:8765 -v "/$(pwd -W):/source" -it klavins/enviro:alpha bash
    esm start
    enviro

If you are using Windows system, using this command

    winpty docker run -p80:80 -p8765:8765 -v $PWD:/source -it klavins/enviro:v1.61 bash
    

run and/or use the project
===
When you enter the "enviro" command, the project runs automatically.

Sources:
===
- The below link from allaboutcircuits.com was used as the coneptual basis for the wall following code implemented for this project. The truth table supplied was the main resource utilized.
https://www.allaboutcircuits.com/projects/how-to-build-a-robot-follow-walls/
- This project uses Enviro and Elma provided through the EEP 520 course
