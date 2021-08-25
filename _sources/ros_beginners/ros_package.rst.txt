.. _ros_package:

Membuat ROS Package
===================

ROS package adalah sebuah `directory` dimana source dari software itu berada. 
Selain itu, library, dataset, message, service, dan action files, `third-party` 
modules juga berada di dalam directory tersebut. Lebih detail mengenai ROS 
package bisa di baca lebih lengkap `disini <http://wiki.ros.org/Packages>`_.

Berikut contoh membuat ROS package

.. code-block:: bash

  #cd ke catkin workspace, kemudian src
  cd ros_catkin_ws/src

  #add required libraries as arguments for catkin_create_pkg
  catkin_create_pkg rospy roscpp std_msgs 

Dengan command `catkin_create_pkg`, `CMakeLists.txt` dan `package.xml` akan 
terbuat otomatis dan `dependencies` yang di berikan pada command tersebut 
secara otomatis akan ada di dalam kedua file tersebut.

CMakeLists.txt
--------------

Berikut adalah contoh `CMakeLists.txt` pada package  
`roscpp_simple_service_client <https://github.com/elmurobotik/ros-tutorials/tree/master/ros-beginners/roscpp_simple_service_client>`_.

.. literalinclude:: ../../../ros-tutorials/ros-beginners/roscpp_simple_service_client/CMakeLists.txt
  :language: bash
  :lineno-start: 0
  :linenos:


package.xml
-----------

Semua dependencies yang dibutuhkan dari package tersebut harus di definisikan dalam file ini.

Berikut adalah contoh `package.xml` pada package  
`roscpp_simple_service_client <https://github.com/elmurobotik/ros-tutorials/tree/master/ros-beginners/roscpp_simple_service_client>`_.

.. literalinclude:: ../../../ros-tutorials/ros-beginners/roscpp_simple_service_client/package.xml
  :language: bash
  :lineno-start: 0
  :linenos: