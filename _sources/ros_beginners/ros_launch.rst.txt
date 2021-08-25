.. _ros_launch:

ROS Launch
==========

**roslaunch** merupakan sebuah tool untuk mengeksekusi satu atau beberapa nodes
sekaligus. Launch file bisa ditulis menggunakan format XML. 
Beberapa fitur roslaunch:

* Setting parameter
* Auto respawn jika node died
* Remap topik
* Setting namespace untuk topik
* Enable gdb debug untuk C++

Berikut adalah contoh roslaunch untuk menjalankan simple_server node C++ dan Python:

Simple roslaunch
----------------

.. literalinclude:: ../../../ros-tutorials/ros-beginners/simple_roslaunch/ros/launch/simple_server.launch
  :language: xml
  :lineno-start: 0
  :linenos:

* Argumen:

  * **pkg**: nama package
  * **type** : nama executable filenya seperti yang di CMakeLists.txt untuk C++ dan sesuai dengan nama file untuk Python
  * **name** : name dari nodenya (tidak harus sama dengan nama executable atau nama filenya)
  * **output** : menampilkan seluruh stdout/stderr ke terminal (opsional)

Roslaunch parameter dan argumen
-------------------------------

.. literalinclude:: ../../../ros-tutorials/ros-beginners/simple_roslaunch/ros/launch/simple_client_with_param_cpp.launch
  :language: xml
  :lineno-start: 0
  :linenos:  

* Argumen untuk param:
  
  * **arg**: memungkinkan passing argument melalui terminal
  * **name**: nama parameter
  * **value** : default value untuk parameter tersebut