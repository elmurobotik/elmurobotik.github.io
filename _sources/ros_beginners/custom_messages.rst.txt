.. _custom_messages:

Kostum messages, srv dan action
===============================

Kostum msg, srv dan action standar nya ditempatkan di package yang berbeda.
Misalnya dalam projek ini, mereka akan di tempatkan di package *ros_custom_msgs*.

.. code-block:: bash

    catkin_create_pkg ros_custom_msgs std_msgs message_generation

Setelah itu kita bisa edit CMakeLists.txt dan package.xml seperti berikut ini:

.. literalinclude:: ../../../ros-tutorials/ros-beginners/ros_custom_msgs/CMakeLists.txt
    :language: bash
    :lineno-start: 0
    :linenos:

File srv yang sudah dibuat (lihat subsection :ref:`membuat_kostum_srv_file`), 
kemudian di tambahkan ke *add_service_files*. Begitu pula dengan msg dan action
files.

.. literalinclude:: ../../../ros-tutorials/ros-beginners/ros_custom_msgs/package.xml
    :language: xml
    :lineno-start: 0
    :linenos:

Untuk membuat sebuah kostum srv file, kita memerlukan *build dependency* pada *message_generation*
dan *runtime atau execution* dependency pada *message_generation* runtime.

Tree structure dari kostum messages, srv dan action files:

.. code-block:: none

    $ tree ros_custom_msgs/
    ros_custom_msgs/
    ├── action
    ├── CMakeLists.txt
    ├── msg
    ├── package.xml
    └── srv
        └── CountWords.srv

.. _membuat_kostum_srv_file:

Membuat kostum srv file
-----------------------

*Service definition* atau *srv* file merupakan sebuah list dari berbagai macam
ROS messages dan digunakan oleh service. Perbedaannya dengan message (*msg*) file adalah srv file memiliki
request dan response yang dipisahkan dengan **---**. Standar penamaan srv file diawali
dengan predikat (verb), misalnya : *CountWords, RecognizeObject, ComputeIK*. 

Berikut adalah contoh dari sebuah service file dengan request sebuah kalimat (*String*) dan response nya 
adalah jumlah kata (*Int32*) dalam kalimat tersebut.

.. code-block:: bash

    std_msgs/string words
    ---
    std_msgs/Int32 num_words

Membuat kostum msg file
-----------------------

ToDo

Membuat kostum action file
--------------------------

ToDo

Kemudian build package *ros_custom_msgs*:

.. code-block:: bash

    catkin build ros_custom_msgs

Verifikasi msg, srv atau action kita sudah ready:

.. code-block:: bash 

    $ rossrv show CountWords
    [ros_custom_msgs/CountWords]:
    std_msgs/String words
    string data
    ---
    std_msgs/Int32 num_words
    int32 data