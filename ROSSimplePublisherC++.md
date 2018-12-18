0. $ cd ~/catkin_ws/src
1. $ catkin_create_pkg test_cpp roscpp std_msgs
2. $ cd ..
3. $ catkin_make
4. $ roscd test_cpp/src
5. $ vim test.cpp

#include <ros/ros.h>
#include <std_msgs/Int32.h>

int main(int argc, char ** argv)
{
     //Initialize and start the node
     ros::init(argc, argv, "abc");
     ros::NodeHandle nh;
     ros::Publisher pub = nh.advertise<std_msgs::Int32>("abc_topic", 1000);
     //Define and create some messages
     std_msgs::Int32 abc;
     abc.data = 0;

     ros::Rate(200);

     while(ros::ok)
     {
           pub.publish(abc);
           ros::spinOnce();
     }

 }

6. $ cd ..
7. $ vim CMakeLists.txt

  cmake_minimum_required(VERSION 2.8.3)
  project(test_cpp)

  find_package(catkin REQUIRED COMPONENTS roscpp )
  catkin_package()
  include_directories(${catkin_INCLUDE_DIRS} )

  add_executable(${PROJECT_NAME}_node src/test_cpp_node.cpp)
  target_link_libraries(${PROJECT_NAME}_node
  ${catkin_LIBRARIES}
)

8. 이 파일은 변경할 필요x
  $ vim package.xml

  <?xml version="1.0"?>
  <package format="2">
    <name>test_cpp</name>
    <version>0.0.0</version>
    <description>The test_cpp package</description>
    <maintainer email="haei3@todo.todo">haei3</maintainer>

    <license>TODO</license>

    <buildtool_depend>catkin</buildtool_depend>
    <build_depend>roscpp</build_depend>
    <build_depend>std_msgs</build_depend>
    <build_export_depend>roscpp</build_export_depend>
    <build_export_depend>std_msgs</build_export_depend>
    <exec_depend>roscpp</exec_depend>
    <exec_depend>std_msgs</exec_depend>

    <export></export>
  </package>

9. roscore
10. rosrun test_cpp test_cpp_node
