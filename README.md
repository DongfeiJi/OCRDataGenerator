# OCR
CTPN+Densenet+CTC  
1，基于CTPN进行文本检测  
2，基于Densenet+CTC进行文本识别  
        
          
第一部分（CTPN):   
CTPN步骤：  
1.首先，用VGG16的前5个Conv stage得到 feature map，大小为 W×H×C。  
2.用3×3的滑动窗口在前一步得到的 feature map上提取特征，利用这些特征来对多个 anchor进行预测,这里 anchor定义与之前 faster-rcnn中的定义相同，也就是帮我们去界定出目标待选区域。  
3.将上一步得到的特征输入到一个双向的 LSTM中，输出 W×256的结果，再将这个结果输入到一个512维的全连接层。  
4.最后通过分类或回归得到的输出主要分为三部分，根据上图从上到下依次为2k vertical coordinates（表示选择框的高度和中心的y轴的坐标）；2k scores（表示的是k个 anchor的类别信息，说明其是否为字符）；k side-refinement（表示的是选择框的水平偏移量）。本文实验中anchor的水平宽度都是16个像素不变。  
5.用文本构造的算法，将我们得到的细长的矩形合并成文本的序列框。  
重点:  
1.anchor:和 Faster-Rcnn中的RPN的主要区别在于引入了微分思想，将我们的的候选区域切成长条形的框来进行处理。k个 anchor（也就是k个待选的长条预选区域）的设置如下：宽度都是16像素，高度从11~273像素变化（每次乘以1.4）。  
2.RNN用于记录上一时刻状态，LSTM长短记忆之前的状态信息，BLSTM（双向LSTM）可以长短记忆之前和之后的状态信息。   
3.anchor文本框的合并，主要是采用pairs的形式。  
        
            
第二部分（Densenet）：  
待补充  
