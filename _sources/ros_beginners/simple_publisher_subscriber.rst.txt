.. _simple_publisher_subscriber:

Topics (Publisher-Subscriber)
=============================

`Topic` dapat digunakan oleh node untuk berkomunikasi satu sama lain. 
Setiap topik di berisi informasi yang bersesuaian dengan tipe message yang digunakan. 
Misalnya sebua `message_a` yang berisi satu variable integer dan satu variable string, 
di publish oleh sebuah `topic_a`, kemudian setiap node yang men-subscribe ke `topic_a` 
tersebut harus juga memiliki tipe `message_a`. Satu node bisa mem-publish lebih 
dari satu topic dan bisa men-subscribe lebih dari satu topic. 

Salah satu kelebihan `Topic` dibandingkan `Service` adalah bawha `Topic` merupakan 
`non-blocking communication type`, yang berarti program bisa terus dieksekusi.

Contoh `nodes` yang berkomunikasi via topics:

Publisher-Subscriber Python
---------------------------

  Node `simple_publisher.py <https://github.com/elmurobotik/ros-tutorials/blob/master/ros-beginners/rospy_simple_publisher_subscriber/ros/scripts/simple_publisher.py>`_ 
  akan `publish` `String` message ke topic `/rospy_pub_sub/event_out`

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/rospy_simple_publisher_subscriber/ros/scripts/simple_publisher.py
    :language: python
    :lineno-start: 0
    :linenos:

  Dan node `simple_subscriber.py <https://github.com/elmurobotik/ros-tutorials/blob/master/ros-beginners/rospy_simple_publisher_subscriber/ros/scripts/simple_subscriber.py>`_ 
  akan `subscribe` `String` message ke topic `/rospy_pub_sub/event_out`

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/rospy_simple_publisher_subscriber/ros/scripts/simple_subscriber.py
    :language: python
    :lineno-start: 0
    :linenos:

  Dimana:

  * `pub_sub_callback`: adalah `callback` dari subscribernya.

Publisher-Subscriber C++
------------------------
  Sama halnya dengan Python code diatas, `simple_publisher.cpp <https://github.com/elmurobotik/ros-tutorials/blob/master/ros-beginners/roscpp_simple_publisher_subscriber/ros/src/simple_publisher.cpp>`_ 
  akan `publish` `String` message ke topic `/rospy_pub_sub/event_out`

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/roscpp_simple_publisher_subscriber/ros/src/simple_publisher.cpp
    :language: c++
    :lineno-start: 0
    :linenos:

  Sedangkan node `simple_subscriber.cpp <https://github.com/elmurobotik/ros-tutorials/blob/master/ros-beginners/roscpp_simple_publisher_subscriber/ros/src/simple_subscriber.cpp>`_ 
  akan `subscribe` `String` message ke topic `/rospy_pub_sub/event_out`

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/roscpp_simple_publisher_subscriber/ros/src/simple_subscriber.cpp
    :language: c++
    :lineno-start: 0
    :linenos: