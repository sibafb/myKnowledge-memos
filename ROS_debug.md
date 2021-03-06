## Topic解析関連

- [ROSにおけるノード間通信の分析に使うコマンド紹介とその実用例](https://kazuyamashi.github.io/ros_lecture/ros_measure.html)  


- ROS node info
```
rosnode info [node name]
```

## Logger 関連

#### コード中に記載し、処理中の値を表示するもの
- ROS Logger  
　　ROS_DEBUG, ROS_INFO, ROS_WARN, ROS_ERROR, ROS_FATAL の5段階がある。  
  - [ROS講座06 ROS Logger](https://qiita.com/srs/items/47e5fd8fe994431d92b7)  
- rospy.loginfo  
  - [HARD2021:ルンバの位置をPythonプログラムで知ろう！](https://demura.net/robot/hard/20085.html) ではrospy.loginfo が使われていた。  
  - [rospyでログを取得する](http://wiki.ros.org/ja/rospy_tutorials/Tutorials/Logging) 公式解説  

#### rosのtopicごと保存する

- rosbag  
    rosのトピックを保存するもの
  - [ROS講座29 rosbagを使う](https://qiita.com/srs/items/f6e2c36996e34bcc4d73)
  - [rosbag - ROS Wiki](http://wiki.ros.org/rosbag)

- rosbagのフィルタツール

  - [ROSのbagファイルのトピックを簡単にフィルタリングするGUIツールを作った](https://myenigma.hatenablog.com/entry/2016/02/09/223403)

- rosbagから画像抽出 
  - [ROSBagから画像を抽出する（image_viewを使うべきではない気がする）](https://ossyaritoori.hatenablog.com/entry/2019/04/03/ROSBag%E3%81%8B%E3%82%89%E7%94%BB%E5%83%8F%E3%82%92%E6%8A%BD%E5%87%BA%E3%81%99%E3%82%8B%EF%BC%88image_view%E3%82%92%E4%BD%BF%E3%81%86%E3%81%B9%E3%81%8D%E3%81%A7%E3%81%AF%E3%81%AA%E3%81%84%E6%B0%97)


#### テンプレ(少し冗長に)
- rosnode list でノードの一覧を調べる。  
```
rosnode list 
---

```

- rosnode info でPublicationとSubscriptionを調べる。
```
rosnode info 
---

```
- rostopic list で配信されているtopicを調べる。
```
rostopic list
---

```
- rostopic info で配信されているtopicのメッセージ型を調べる。
```
rostopic info
---
$rostopic info /create1/odom
Type: nav_msgs/Odometry

Publishers: 
 * /gazebo (http://aki-desktop:46081/)

Subscribers: 
 * /create1/nodelet_manager (http://aki-desktop:41267/)

```

- rosmsgs show  でtopicのメッセージ型の構造がわかる
```
rosmsg show
---
$rosmsg show nav_msgs/Odometry
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string child_frame_id
geometry_msgs/PoseWithCovariance pose
  geometry_msgs/Pose pose
    geometry_msgs/Point position
      float64 x
      float64 y
      float64 z
    geometry_msgs/Quaternion orientation
      float64 x
      float64 y
      float64 z
      float64 w
  float64[36] covariance
geometry_msgs/TwistWithCovariance twist
  geometry_msgs/Twist twist
    geometry_msgs/Vector3 linear
      float64 x
      float64 y
      float64 z
    geometry_msgs/Vector3 angular
      float64 x
      float64 y
      float64 z
  float64[36] covariance

```

- rostopic echo でメッセージ型の中身も指定して取得できる。
```
rostopic echo /create1/odom/pose/pose/position/x
---
0.284454533782
---
0.284454555459
---
・・・
```

- rosbag で取得したいトピックのログを保存できる。  
```
rosbag record /create1/odom/pose/pose/position/x /create1/odom/pose/pose/position/y 
```
保存ファイル名を指定可能
```
rosbag record -O file.bag
```

#### rosgraph

```
rosgraph
```

#### vscodeでrosをステップ実行してデバッグ

[vscodeでrosをステップ実行してデバッグ](https://qiita.com/taka_horibe/items/50e4659e88d1ee3cd04a)

[Debug ROS nodes with vscode-ros](https://github.com/ms-iot/vscode-ros/blob/master/doc/spec/debug-ros-nodes.md)

#### 

[ROSのC++のソースコードをgdbでデバッグする方法](https://qiita.com/Nasupl_r/items/7610139628fc59d47cb5)

#### 調査記事

- [ROS topicのプロット方法色々](https://qiita.com/FluffyHernia/items/88d67195eb6c903ed942)  
  rqt_plot, rqt_bag, Plot juggler, rosbagを吐き出してからシェルスクリプトで変換など。
  
- [ROSの便利機能](https://gbiggs.github.io/ros_moveit_rsj_tutorial/ros_useful_stuff.html)

#### 参考資料

- [TIER IV ACADEMY 自動運転システム構築塾](http://4c281b16296b2ab02a4e0b2e3f75446d.cdnext.stream.ne.jp/randc/mirai/2-1%20catkin.pdf)  
- [ROS 勉強記録 (OTL)](http://ros-robot.blogspot.com/)
- [安曇野の森から > ROS(Robot Operating System)を使う](http://forestofazumino.web.fc2.com/ros/ros_top.html)  
- [ROSにおけるノード間通信の分析に使うコマンド紹介とその実用例](https://kazuyamashi.github.io/ros_lecture/ros_measure.html)
- [東大JSKが公開しているクールなROS可視化ライブラリを使ってみる](https://myenigma.hatenablog.com/entry/2015/10/30/223023)

