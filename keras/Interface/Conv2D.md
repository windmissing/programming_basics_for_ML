# tf.nn.conv2d

```python
tf.nn.conv2d(input,  # 张量输入
            filter, # 卷积核参数
            strides, # 步长参数
            padding, # 卷积方式
            use_cudnn_on_gpu=None, # 是否是gpu加速
            data_format=None,  # 数据格式，与步长参数配合，决定移动方式
            name=None) # 名字，用于tensorboard图形显示时使用
```

# tf.layers.conv2d

```python
conv2d(inputs, # 输入的张量
　　 filters, # 卷积过滤器的数量
    kernel_size, # 卷积窗口的大小，一个整数：表示宽高相等；两个整数的元组/队列：分别为宽和高
    strides=(1, 1), # 卷积步长
    padding='valid', # 可选，默认为 valid，padding 的模式，有 valid 和 same 两种，大小写不区分。
    data_format='channels_last', # 可选，默认 channels_last，分为 channels_last 和 channels_first 两种模式，代表了输入数据的维度类型，如果是 channels_last，那么输入数据的 shape 为 (batch, height, width, channels)，如果是 channels_first，那么输入数据的 shape 为 (batch, channels, height, width)
    dilation_rate=(1, 1),# 可选，默认为 (1, 1)，卷积的扩张率，如当扩张率为 2 时，卷积核内部就会有边距，3×3 的卷积核就会变成 5×5。
    activation=None, # 可选，默认为 None，如果为 None 则是线性激活。
    use_bias=True, # 可选，默认为 True，是否使用偏置。
    kernel_initializer=None, # 可选，默认为 None，即权重的初始化方法，如果为 None，则使用默认的 Xavier 初始化方法。
    bias_initializer=<tensorflow.python.ops.init_ops.Zeros object at 0x000002596A1FD898>, # 可选，默认为零值初始化，即偏置的初始化方法。
    kernel_regularizer=None,# 可选，默认为 None，施加在权重上的正则项。
    bias_regularizer=None, # 可选，默认为 None，施加在偏置上的正则项。
    activity_regularizer=None, # 可选，默认为 None，施加在输出上的正则项。
    kernel_constraint=None, # 可选，默认为 None，施加在权重上的约束项。
    bias_constraint=None, # 可选，默认为 None，施加在偏置上的约束项。
    trainable=True, # 可选，默认为 True，布尔类型，如果为 True，则将变量添加到 GraphKeys.TRAINABLE_VARIABLES 中。
    name=None, # 可选，默认为 None，卷积层的名称。
    reuse=None) # 可选，默认为 None，布尔类型，如果为 True，那么如果 name 相同时，会重复利用。
```

# keras.layers.conv2d

```python
keras.layers.convolutional.Conv2D(filters,
    kernel_size, #卷积窗口的大小，一个整数：表示宽高相等；两个整数的元组/队列：分别为宽和高
    strides=(1, 1), # 单个整数或由两个整数构成的list/tuple，为卷积的步长。如为单个整数，则表示在各个空间维度的相同步长。任何不为1的strides均与任何不为1的dilation_rate均不兼容
　　padding='valid', 
　　data_format=None,
　　dilation_rate=(1, 1),
　　activation=None, 
　　use_bias=True, 
　　kernel_initializer='glorot_uniform', 
　　bias_initializer='zeros', 
　　kernel_regularizer=None,
 　 bias_regularizer=None, 
　　activity_regularizer=None, 
　　kernel_constraint=None, 
　　bias_constraint=None)
```

# 接口比较

||tf.nn.conv2d|tf.layers.conv2d|tf.keras.layers.conv2d|
|---|---|---|---|
|输入的张量|input<br>`input.shape=[batch, in_height, in_width, in_channels]`|inputs<br>`inputs.shape=[batch, in_height, in_width, in_channels]`|无，通过框架自动传入数据，不需要显式地定义输入数据是什么|
|卷积过滤器的数量|filter<br>`filter.shape=[filter_height, filter_width, in_channels, out_channels]`<br>filter.shape[3]代表卷积过滤器的数量|filters|filters|
|卷积窗口的大小|filter<br>`filter=[filter_height, filter_width, in_channels, out_channels]`<br>filters.shape[0]和filters.shape[1]代表卷积窗口的大小|kernel_size|kernel_size|
|卷积步长|`strides = [1, stride, stride, 1]`<br>第0项和第3项必须为1，中间2项为卷积步长|strides=(1, 1)|strides=(1, 1)|
|padding 的模式|padding|padding='valid'|padding='valid'|
|是否使用偏置|无，如果需要，可以写成`tf.nn.conv2d(...) + b`|use_bias=True|use_bias=True|
|