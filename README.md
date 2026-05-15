# Robot
from lesson_header import *

# Variables
number_of_obstacles = 4
warning_distance = 15
obstacle_count = 0
dict = {
    "blue": (0, 0, 255),
    "red": (255, 0, 0)
}
# Function ideas
def show_progress():
     print(f"it has passed {obstacle_count} out of {number_of_obstacles}")     
def check_move():
    global obstacle_count
    if (obstacle_count == 0 or obstacle_count == 2):
        eyes.set_both(*dict["blue"])
        dict["blue"] = 0, 0, 120
        moves.move_right(1.5)
    elif (obstacle_count == 1 or obstacle_count == 3):
        eyes.set_both(*dict["red"])
        dict["red"] = 120, 0, 0
        moves.move_left(1.5)
    moves.forward(1)
    obstacle_count += 1
def choose_move():
 while obstacle_count < number_of_obstacles:
    if sonar.get_distance_cm(filtered=True) > warning_distance:
     moves.forward(0.5)
     print(obstacle_count)
    elif sonar.get_distance_cm(filtered=True) < warning_distance:
     check_move()
# Loop ideas
while obstacle_count < number_of_obstacles:
 choose_move()
