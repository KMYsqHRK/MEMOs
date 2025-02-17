# ROSとArduinoの接続について

https://www.switch-science.com/blogs/magazine/arduino-uno-r4-minima-ros2?srsltid=AfmBOophz4ztDKU8xPMLdeIW2FUepWYGmOegGzTE9loxljcWhnpQTLED

このサイトを参考にしています

## 1. インストールしたもの

- ROS2 humble：ROS2
- micro ROS エージェント：軽量化したROSとROSをつなぐための存在
- micro ROS for Arduino：Arduino用のmicroROSライブラリ.Gitから取得しzipで登録.一部minima用に改変.
- Arduino IDE：公式サイトからV2.3.4をダウンロード

## 2. .bashrcに書き込んだ設定

~~~bash
# for ROS2
source /opt/ros/humble/setup.bash

# for micro ROS
source ~/ros2_ws/install/setup.bash

# for micro ROS
alias mra='ros2 run micro_ros_agent micro_ros_agent serial --dev /dev/ttyACM0 -b 921600'
~~~

## 3. bashでの実行コマンド

~~~bash
mra #エイリアスに設定済み。micro ROSエージェントの起動

#その後スケッチをArduinoに書き込み
~~~

`ros2 topic echo /micro_ros_arduino_node_publisher`を 他のターミナルで実行すると結果が得られます。
