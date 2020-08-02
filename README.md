# yolov5_2.0-TensorRt
U版yolov5 2.0的tensorrt加速



并且对resize和图像处理阶段的操作左右优化，再win环境下debug下速度有很大提升，但是release则没有变化，因为在release时，opencv中会有相应的优化操作。

```
实际上，at操作符与ptr操作符在Debug版本下都是有内存检查、防止操作越界的操作，而data十分简单粗暴，没有任何检查，由于它的简单粗暴所以使得data操作速度很快。所以在Debug版本下，at操作符与ptr操作符相较于data，速度还是慢了不少。

另外在Debug版本下，at操作要比指针操作慢得多，所以对于不连续数据或者单个点处理，可以考虑at操作，对于连续的大量数据，尽量不要使用它。
```

感谢下面两个开源实现：

 https://github.com/wang-xinyu/tensorrtx

https://github.com/AIpakchoi/yolov5_tensorrt