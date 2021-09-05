## [ORB-SLAM 公式project webpage](https://webdiis.unizar.es/~raulmur/orbslam/)  
公式ソースコード  
ORB-SLAM: https://github.com/raulmur/ORB_SLAM . (Monocular. ROS integrated)  
ORB-SLAM2: https://github.com/raulmur/ORB_SLAM2 . (Monocular, Stereo, RGB-D. ROS optional)  
ORB-SLAM 3.0 (beta):https://github.com/UZ-SLAMLab/ORB_SLAM3 (Visual-Inertial and Multi-Map SLAM)  

## 論文  
R. Mur-Artal, J. M. M. Montiel, and J. D. Tardos, "ORB-SLAM: a versatile and accurate monocular SLAM system." arXiv preprint arXiv:1502.00956, pp.1-15, 2015.

## 解説記事メモ
#### 趣味なし奴のメモ帳/ORB-SLAMの特徴 2017/07/08の記事： [https://noshumi.blogspot.com/2017/07/orb-slam.html](https://noshumi.blogspot.com/2017/07/orb-slam.html)　  
- 特徴量ベースのSLAMで、ORB−SLAMはPTAM(Paraleel Tracking and Mapping)の類型。
- 対するのは輝度を直接用いるもの(direct SLAM)。LSD-SLAMとDTAM(Dense Tracking and Mapping in Real-TIme)。
- 特徴量ベースがvisual SLAMでは主だったが、だんだんdirectの性能が良いことがわかってきたところ、ORB-SLAMが特徴ベースでも性能が良いと示してきた。
- BAによる誤差の吸収、特徴量を使うので回転や光の変化、動的物体に強くなれる、direct側もLoop Closingのために特徴量を使用するので、それと比べると一貫性がある。
- PTAMと同じなのは
  - MappingとTrackingが並列して行われる。
  - BAをリアルタイムで行う。
- PTAMからの変更点は 
  - 特徴点の選び方は比較的高速なFASTを使う.  
  - 見つけた特徴点はロバストさと高速さのバランスの良いORB特徴量で表現　(Rubble)
  - DBoW2というLoop Closingを採用し、ロバスト性向上(Galvez-Lopez and Tardos)
  - BAはg2oフレームワークを使用、実装がしやすい？（Kuemmerle）
  - Covisibility graphの採用により、Loop Closingの検出後、その効果をうまく伝搬できる（Strasd）
- ORB-SLAMでのオリジナルは
  - キーフレームは適者生存、多めに取ることで局所的な高精度、あとから余分なものを削除する
  - 初期化を自動で行う。
- アルゴリズム(ブログの図参照)
  - スレッド3つ、データ（ベース？）が２つ
  - スレッド：TRACKING, LOCAL MAPPING, LOOP CLOSING
    - TRACKINGは、Frameを受け取ってKeyFlameをLOCAL MAPPINGに渡す。 
    - TRACKINGは、ExtractORB　>> Initial Pose Estimation from last frame or Relacalisation >> Track Local Map >> New KeyFrame Decision を行う。
    - LOCAL MAPPINGは、 KeyFrameInsersion >> RecentMappointsculling >> NewPointsCreation >> LocalBA >> LocalKeyFramesCulling  を行う。
    - LOOP CLOSINGは、　(LOOP Detection Start)Candidates Detection >> ComputeSim3 (LOOP Detection End)>>(LOOP Correction Start)Loop Fusion >> Optimize Essential Graph (LOOP Correction End)
  - データ:PLACE RECONGNITION, MAP 

## 用語  
- 特徴量ってなに

- BA(Bundle Adjustment)
- FAST
- ORB特徴量
- DBoW2
- g2oフレームワーク
- Covisibility graph
- キーフレーム




