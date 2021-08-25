.. _simple_service_client:

Services (Server-Client)
========================

Service merupakan cara lain untuk passsing data antar node dalam ROS. Service 
memungkinkan salah satu node untuk memanggil sebuah fungsi dari node yang lain.
Layanan service itu sendiri di atur oleh server node, yang merupakan tempat dimana
callback di panggil. Sedangkan request untuk layanan service di panggil
oleh client node. 

Berbeda dengan topics, service adalah layanan *blocking call*,
dimana pemrosesan di node tersebut akan terhenti sampai servernya menyelesaikan
request dari client. Jadi, services seharusnya tidak digunakan untuk
layanan yang memerlukan komputasi yang lama. Salah satu penggunanaan service
misalnya untuk melakukan komputasi Inverse Kinematic (IK), inference (object classsification).

.. hint:: ROS command line tools yang bisa digunakan
  
  * rossrv: untuk melihat informasi yang berhubungan dengan srv file definition.
  * rosservice: untuk melihat dan berinteraksi dengan service tersedia. 

**Service definition file (srv)**
---------------------------------

srv file memiliki kesamaan struktur seperti msg file. Namun, srv memiliki 
request dan response. Sebagai contoh, misalnya kita akan membuat service untuk
menghitung jumlah kata pada kalimat yang diberikan, maka langkah pertama kita
perlu membuat service file *CountWords.srv* dimana input nya adalah kalimat, 
dan output nya adalah jumlah kata dalam kalimat tersebut. Request dan response
dalam service file di pisahkan dengan **---**.

.. code-block:: bash

  std_msgs/string words
  ---
  std_msgs/Int32 counts

Standar penamaan service file selalu di mulai dengan predikat (verb), misalnya
*CountWords, RecognizeImage, ComputeIK*.

Request juga bisa lebih dari satu message, begitu pula responnya. Misalnya
kita mau menambahkan opsi (*count_articles*) apakah kita mau menghilangkan artikel dalam kalimat
tersebut. Sementara di responnya, kita juga bisa menambahkan jumlah artikelnya.

.. code-block:: bash

  std_msgs/string words
  std_msgs/Bool count_articles
  ---
  std_msgs/Int32 num_words
  std_msgs/Int32 num_articles

Selanjutnya kita bisa menambahkan *CountWords.srv* ke CMakeList untuk di compile.
Penjelasan lebih lanjut mengenai kompilasinya, di jelaskan 
disini :ref:`custom_messages`

Server-Client Python
--------------------

Pertama kita perlu membuat ROS package baru dengan nama *rospy_simple_service_server*.
Jika belum paham tentang paham tentang packages, silahkan buka :ref:`ros_package`.

.. code-block:: bash

  catkin_create_package rospy_simple_service_client rospy ros_custom_msgs

Server (*simple_server.py*) dan client node (*simple_client.py*) akan tempatkan di package ini.


* Python server node

  Sama halnya dengan topic, server di dalam service juga menggunakan mekanisme
  *callback*. Server menyediakan callback dan akan di panggil ketika request
  diterima. Berikut adalah contoh service untuk menghitung jumlah kata menggunakan
  python dan cpp.

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/rospy_simple_service_client/ros/scripts/simple_server.py
    :language: python
    :lineno-start: 0
    :linenos:

  *simple_server.py* harus executable dengan cara:

  .. code-block:: bash

    chmod +x simple_server.py

  Kemudian jalankan node:

  .. code-block:: bash

    rosrun rospy_simple_service_client simple_server.py

  Untuk memastikan service server berjalan dengan baik, kita bisa mengeceknya via
  terminal.

  .. code-block:: bash

    emha at ThinkPad-E570 in ~$ rosservice list
        /rosout/get_loggers
        /rosout/set_logger_level
        /rospy_simple_server_node/get_loggers
        /rospy_simple_server_node/set_logger_level
        /rospy_word_count



* Python client node

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/rospy_simple_service_client/ros/scripts/simple_client.py
    :language: python
    :lineno-start: 0
    :linenos:    

Server-Client C++
-----------------

* C++ Server node

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/roscpp_simple_service_client/ros/src/simple_server.cpp
    :language: C++
    :lineno-start: 0
    :linenos:
    
* C++ Client node

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/roscpp_simple_service_client/ros/src/simple_client.cpp
    :language: C++
    :lineno-start: 0
    :linenos:

Contoh CMakeList.txt

  .. literalinclude:: ../../../ros-tutorials/ros-beginners/roscpp_simple_service_client/CMakeLists.txt
    :language: bash
    :lineno-start: 0
    :linenos:
