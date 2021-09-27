# roslaunch

- [roslaunchXML](http://wiki.ros.org/roslaunch/XML)

- [ROS講座04 roslaunch1](https://qiita.com/srs/items/d7b0be3392a3a224b02f)

- [ROS講座19 roslaunch2](https://qiita.com/srs/items/e7882078b8cf11dc51fb)
- [Record with rosbag from launch file](https://answers.ros.org/question/52773/record-with-rosbag-from-launch-file/#:~:text=Record%20with%20rosbag%20from%20launch%20file)
```
 <node pkg="rosbag" type="record" name="rosbag_record_hrpsys"
       args="record -o /tmp/hrp2-hrpsys /imu /joint_states /joint_command /force_0 /force_1 /force_2 /force_3 /base_link"
       if="$(arg record_hrpsys)" />
```

- [How to play rosbag using launch file ?](https://answers.ros.org/question/62811/how-to-play-rosbag-using-launch-file/)
- 
- [rosbagの便利オプション](https://ppdr.softether.net/ros-rosbag-options)
下記が使えそう
>トピック名をリネームして再生
```
rosbag play test.bag tf:=tf_old
```
- [データを記録し，リプレイをする](http://wiki.ros.org/ja/ROS/Tutorials/Recording%20and%20playing%20back%20data)

- [【ROS】一つのlaunchファイルで複数のロボット・PCを動かす](https://b.ueda.tech/?post=20190706_ros)

- [大きなプロジェクトにおける roslaunch の tips](http://wiki.ros.org/ja/roslaunch/Tutorials/Roslaunch%20tips%20for%20larger%20projects)

- [ROS自動データ作成のススメ](https://tenteroring.org/tenteroring/2020/11/2082)
