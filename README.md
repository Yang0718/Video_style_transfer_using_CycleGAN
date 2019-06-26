# <center>Video Style Transfer<center>
這學期在交大電信所修「深度學習」，將期末專題的成果整理，供大家參考。<br>
(題外話，這堂課很棒，簡老師教得很好)<br>

主題是影片的風格轉換，架構CycleGAN網路上很多介紹，不再贅述。<br>
模型架構的部分則取自此github:https://github.com/tjwei/GANotebooks <br>

首先準備兩個影片：
1. 女生唱學貓叫
2. 男生拿著香蕉與麥克風唱國旗歌(手邊剛好只有這兩個東西)<br>

期望模型在訓練後能輸出假影片：
1. 女生唱國旗歌
2. 男生拿著香蕉與麥克風學貓叫

如果你想要用自己的影片來訓練，就先用ffmpeg將影片切成一張張的照片，存到'frames'資料夾中，再去執行程式。
```
ffmpeg -i video.mp4 outputfile/%1d.png 
```
[我們的數據集 Download our dataset](https://drive.google.com/open?id=1XE1Z9AK1l0s9wq5OXc5NbAgYG7YKfaS4)<br>
[訓練好的模型檔 Download model file](https://drive.google.com/open?id=1VdXNCqYh_d7YlUVVhOPFQuUg5iYhLMyW)

## Demo
[https://www.youtube.com/watch?v=7Ohd2JoBGJM](https://www.youtube.com/watch?v=7Ohd2JoBGJM)<br>

![demo](https://github.com/Yang0718/Video_style_transfer_using_CycleGAN/raw/master/figures/youtube.PNG)<br>

## Training
將照片都reshape至256x256，使用2080 Ti 跑30個epochs費時近3小時。<br>
也可以嘗試128x128，模型更容易訓練得好，轉換效果更逼真<br>
只是因為怕用128輸出的影片畫質太差，在期末課堂demo投影出來太模糊，所以這邊才使用256<br>

**Training results in different epochs**<br>
由上而下依序為Input, Fake, Reconstruct<br>
![epoch_0](https://github.com/Yang0718/Video_style_transfer_using_CycleGAN/raw/master/figures/training_result_0.PNG)
![epoch_15](https://github.com/Yang0718/Video_style_transfer_using_CycleGAN/raw/master/figures/training_result_15.PNG)
![epoch_30](https://github.com/Yang0718/Video_style_transfer_using_CycleGAN/raw/master/figures/training_result_30.PNG)

## Interesting fake images<br>
巨量的香蕉與麥克風<br>
女生逐漸變成男生的藍色(風格轉換到一半)<br>
憑空多一根香蕉<br>
![interesting](https://github.com/Yang0718/Video_style_transfer_using_CycleGAN/raw/master/figures/interesting.PNG)


