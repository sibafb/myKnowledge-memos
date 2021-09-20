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

