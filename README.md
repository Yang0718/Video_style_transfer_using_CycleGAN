# <center>Video Style Transfer
這學期在交大電信所修「深度學習」，將期末專題的成果整理，供大家參考。<br>
(題外話，這堂課很棒，簡老師教得很好)<br>

主題是影片的風格轉換，架構CycleGAN網路上很多介紹，不再贅述。<br>
首先準備兩個影片：
1. 女生學貓叫
2. 男生拿著香蕉與麥克風唱國旗歌(手邊剛好只有這兩個東西)<br>

期望輸出：
1. 女生唱國旗歌
2. 男生拿著香蕉與麥克風學貓叫

如果你想要用自己的影片來訓練，就先用ffmpeg將影片切成一張張的照片，存到'frames'資料夾中，再去執行程式。
```
ffmpeg -i video.mp4 outputfile/%1d.png 
```
[我們的數據集](https://drive.google.com/open?id=1yg03hR8XEsVv-c819naRGJ4jGVJSxr7X)

## Training
將照片都reshape至256x256，使用2080 Ti 跑30個epochs費時近3小時。<br>
也可以嘗試128x128，效果會更好，模型更容易訓練得好。只是因為怕用128輸出的影片畫質太差，在期末課堂demo投影出來太模糊，所以這邊才使用256<br>

[成果demo]()

