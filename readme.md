Steps to reproduce the problem

Start the simulation
- roslaunch vrx_gazebo vrx.launch urdf:=/home/twin_n/vrx_ws/my_wamv/my_wamv_3.urdf

Publish tf frames and robot localization
- roslaunch vrx_gazeo localization_example.launch

Start hector slam node
- roslaunch sqwoosh sqwoosh.launch

Run rviz
- rosrun rviz rviz -d (PATH TO vrx_ws)src/sqwoosh/config/rviz.rviz

Run teleop to control the bot
- roslaunch vrx_gazebo usv_keydrive.launch


I'm currently trying to implement ros navigation stack to go from robot's current position to a given gps coordinate. 
Most of the configurations are from vrx_gazebo demo configurations.
From my testing it seems the odometry information is not very reliable especially when i do rotations and it is not consistent enought to build a map.
Is it normal for odometry to drift this much? I've tried removing every noise parameter in plugins in the urdf_file (my_wamv_3.urdf) but the drift still persists
if it is normal for odometry to drift this much, what options do i have?


In real life implementation i was expecting 1-4meter drift in gps value so i thought if i combine it with imu i might manage to reduce the drift to around
2 meters and that should be a reasonable drift for my goal position. i want to use rplidar just to avoid non stationary obstacles in the map like boats running on the river and a static map for path planning.

is it possible to generate a static map without using slam tools? 
is there a better way to approach this problem?