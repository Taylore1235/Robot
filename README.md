# Robot
my code to make a robot move around a group of objects
from lesson_header import *

# Variables
number_of_obstacles = 4
obstacle_count = 0
warning_distance = 20
far_distance = 50

# Function ideas
def show_progress():
     print(f"it has passed {obstacle_count} out of {number_of_obstacles}")
     obstacle_count += 1
     return obstcle_count
def choose_move():
 if sonar.get_distance_cm(filtered=True) > warning_distance:
  moves.forward(0.5)
 elif sonar.get_distance_cm(filtered=True) < warning_distance: 
  moves.move_left(1)
 elif sonar.get_distance_cm(filtered=True) == warning_distance:
  moves.move_right(1)
 else: sonar.get_distance_cm(filtered=True) == 0
 moves.forward(0.1)
# Loop ideas
while obstacle_count < number_of_obstacles:
 choose_move()

#return obstacle_count
#     read sensor
#     decide what to do
#     move
#     update progress
#
# Finish safely when you are done.
stop_project_robot()
