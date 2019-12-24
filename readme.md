# Kinematic parameters 6-dof robots of [fanuc](https://github.com/ros-industrial/fanuc) package

Parameters to solve the inverse kinematics using [opw_kinematics](https://github.com/Jmeyer1292/opw_kinematics).

These files where created using [this](https://github.com/JeroenDM/urdf_to_opw_kinematics) package, with additional manual cleaning. (Noting that cannot be automated, mainly formatting and rounding issues.) These are just the robots from the package with 6 degrees of freedom.

I tested all these parameters using the recently introduced forward kinematic test in the plugin package, in combination with a quick visual check in rviz.

I used the following bash script to extract the robot models from the fanuc package:
```bash
extension=".urdf"
find -name "*.xacro" -not -name "*macro*" -not -name "*common*" | while read line; do
    name=$(basename $line .xacro);
    rosrun xacro xacro --inorder $line > "$name$extension"
done

mv *.urdf ./robot_models
```
