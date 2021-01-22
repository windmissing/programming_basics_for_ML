# tf.nn.avg_pool(

```python    
tf.nn.avg_pool(
    # # 四维张量 [batch, height, width, channels]，数值类型为：float32，float64， qint8， quint8，qint32
    value,
    # 四个整型值 int 的列表或元组，输入张量 value 的每个维度上的滑动窗口的尺寸大小 
    ksize,
    # 四个整型值 int 的列表或元组，输入张量 value 的每个维度上的滑动窗口的步幅长度
    strides,
    # 字符型参数，“VALID” 或 “SAME”，填充算法，参照 tf.nn.convolution
    padding,
    # 字符型参数，“NHWC” 或 “NCHW”，分别代表 [batch, height, width, channels] 和 [batch, height, channels , width]
    data_format='NHWC',
    # 可选参数，操作的名称
    name=None
)
```

# keras.layers.AveragePooling2D

```python
keras.layers.AveragePooling2D(
    #  整数，或者 2 个整数表示的元组， 沿（垂直，水平）方向缩小比例的因数。 （2，2）会把输入张量的两个维度都缩小一半。 如果只使用一个整数，那么两个维度都会使用同样的窗口长度。
    pool_size=(2, 2), 
    # 整数，2 个整数表示的元组，或者是 None。 表示步长值。 如果是 None，那么默认值是 pool_size。
    strides=None,
    # "valid" 或者 "same" （区分大小写）。
    padding='valid', 
    # 字符串，channels_last (默认)或 channels_first 之一。 表示输入各维度的顺序。 channels_last 代表尺寸是 (batch, height, width, channels) 的输入张量， 而 channels_first 代表尺寸是 (batch, channels, height, width) 的输入张量。 默认值根据 Keras 配置文件 ~/.keras/keras.json 中的 image_data_format 值来设置。 如果还没有设置过，那么默认值就是 "channels_last"。
    data_format=None)
```

# 接口比较

||tf.nn.avg_pool|keras.layers.AveragePooling2D|
|---|---|---|
|输入的张量|value|无|
|窗口长度|ksize，通常为[1,x,x,1]|pool_size|
|步幅长度|strides，通常为[1,x,x,1]|strides|
|填充算法|padding|padding|