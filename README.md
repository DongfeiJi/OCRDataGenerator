# OCRDataGenerator
本实验主要是生成OCR相关的数据生成，数据扩充，只需一个命令行即可生成你想要的文本图片，用于训练。
        
### 环境部署
```python
pip install -r requirements.txt
```
  
### 使用说明
1.生成英文文本  
```python
python run.py -w 5 -f 64
```
  
2.生成中文文本，这里我是生成身份证姓名与证件号  
```python
python run.py -l cn -c 100 -w 5
```

3.指令说明   
-l cn  代表中文  
-c 100  代表100张图片  
-w 5  代表文本宽度为5级别  
-k 5  代表文本倾斜角度  
-rk  代表文本随机倾斜   
-bl 1  代表高斯模糊等级  
-rbl  代表随机高斯模糊  
-d  代表弯曲波浪  
-do   代表弯曲波浪  

### 文件说明
1，dicts文件夹用于修改生成你想要内容的，如改变生成的中文汉字内容，只需改变cn.text文件内容。  
2，你同样可以修改你的字体，在fonts文件夹，支持.tff文件。  
  
原项目地址:https://github.com/Belval/TextRecognitionDataGenerator  
