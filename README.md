# Cartographer for Turtlebot

## 1. Hardware Requirement

>* kobuki
>* hokuyo urg laser sensor

## 2. Dependencies

>* [kobuki driver](https://www.ncnynl.com/archives/201611/1103.html)
>* [hokuyo laser driver](https://blog.csdn.net/Buer_zhu/article/details/80945830)
>* [joy stick driver](https://github.com/HuangJianxjtu/joystick). this item is optional but recommended.
>* [cartographer](https://blog.csdn.net/qq_26482237/article/details/92676267?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)

the bugs and solutions you may need:

>* [git problem](https://blog.csdn.net/qq_21508727/article/details/89413590)
>* [website problem](https://www.cnblogs.com/call-me-dasheng/p/12777139.html)


## 3. How to use?

clone this directory into src directory of an isolated catkin workspace (e.g. carto_ws). and return to this workspace, run these commands:
>* `catkin_make_isolated --install --use-ninja`
>* `source install_isolated/setup.bash`


## 4. How to run?

>* `roslaunch cartographer_turtlebot one_command_bringup.launch`
>* `roslaunch cartographer_turtlebot turtlebot.launch`

## 5. How to save the map?

[link](https://www.ncnynl.com/archives/201904/2915.html)

## 6. References

[official cartographer](https://github.com/cartographer-project/cartographer_turtlebot)