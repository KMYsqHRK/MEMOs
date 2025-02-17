# ROS2とMicroRosそれぞれについてわかったこと

## ROS2について

### ROS2_wsについて

新しいROS関連のシステム(microROS-agentなど)が必要にならない限りは触ることは少ない？と思ったが、次の標準メッセージ型に当てはまらないものを送らなければならないとき、c++のプロジェクトである、全体を一つのプロジェクトでまとめたい、ときはビルドが必要になるっぽい。

- std_msgs/Int32 - 整数値
- std_msgs/String - 文字列
- geometry_msgs/Pose - 位置と姿勢
- sensor_msgs/Image - 画像データ

### 必要なsourceについて

`source /opt/ros/humble/setup.bash`が`sorce`されなければROS2のシステムが起きない。
ROS1で言うところのroscoreのようなものか。

次の内容にも関与するが、ここで環境変数に登録されたPython,もしくはPython3とROS2が連携をとれるようになる。

### ROS2のPythonについて

Pythonで比較的簡単にROS2ノードを作成することができる。
ノードを作成し、Pythonで実行するだけでnodeの通信が開始する。

ちなみに、`source /opt/ros/humble/setup.bash` が `sorce` されたときの環境変数のPythonが大事なので、仮想環境のPythonを使いたいときはこのコマンドの前に実行するのが良い。

### Boardレートについて

送信データ量(bit/sec)。送信側と受信側で設定を合わせる必要がある。

`ros2 run micro_ros_agent micro_ros_agent serial --dev /dev/ttyACM0 -b 9600`

の9600がこの値である。

### Micro ROS Agentについて

やはり、先にagentを起動する必要がある。これには注意。

なお、次の関数を.bashrcに設定したので `mra 115200` とかで実行するのが良い感じ

~~~bash
function mra() {
    ros2 run micro_ros_agent micro_ros_agent serial --dev /dev/ttyACM0 -b $1
}
~~~

## 全体の流れの再確認

ここでは、.bashrcに書き込んだ内容は割愛する

1. Micro ROS Agent の起動

    `mra 11520`

2. 別のターミナルでパブリッシャノードの実行

    `Python3 PublisherNode.py`

3. ArduinoIDEからマイコンにビルドと書き出し

これで実行できた





