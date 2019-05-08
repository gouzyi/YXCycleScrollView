# 轮播图

一款简单实用多样式轮播图控件，可自定义样式；支持左右、上下滚动。
# 效果图
![banner.gif](https://i.loli.net/2019/05/08/5cd26bf317b77.gif)

# 特性

- 支持自定义`Cell`
- 支持上下、左右滚动
- 支持滚动缩放效果
- 支持XIB
- 支持设置滚动间隙

# 安装

- ### `CocoaPods`
> pod

- ### 手动安装
> 将工程里`YXCycleScrollView`文件夹直接拖到项目即可




# 使用
- 导入`#import "YXCycleScrollView.h"`

```
 NSArray *images = @[@"http://pic37.nipic.com/20140105/15166348_202320428000_2.jpg",
                        @"http://pic37.nipic.com/20140113/8800276_184927469000_2.png",
                        @"http://img.redocn.com/sheying/20140731/qinghaihuyuanjing_2820969.jpg",
                        @"http://pic29.nipic.com/20130517/9252150_140653449378_2.jpg",
                        @"http://pic36.nipic.com/20131126/8821914_071759099000_2.jpg"
                       ];
    
    NSArray *titles = @[@"我是自定义CollectionViewCell",
                        @"自定义Cell需要设置delegate, 并实现代理方法",
                        @"我是自定义CollectionViewCell",
                        @"自定义Cell需要设置delegate, 并实现代理方法",
                        @"我是自定义CollectionViewCell",
                        ];
    _images = images;
    _titles = titles;
    
    /// 样式一: 动画样式pageControl
    _cycleView1.imagesArray = images;
    __weak typeof(self) weakSelf = self;
    /// 点击事件回调 (支持block和代理)此处用的block
    _cycleView1.clickItemOperationBlock = ^(NSInteger currentIndex) {
        NSLog(@"-------------->点击了第%ld个", (long)currentIndex);
        [weakSelf.navigationController pushViewController:[NSClassFromString(@"CycleScrollViewController") new] animated:YES];
    };
    
    /// 样式二
    YXCycleScrollView *cycleView2 = [[YXCycleScrollView alloc] initWithFrame:CGRectMake(0, 170, kSCREEN_WIDTH, 150)];
    cycleView2.itemSpacing = 0;
    cycleView2.itemSize = CGSizeMake(kSCREEN_WIDTH - 40, cycleView2.frame.size.height);
    cycleView2.imagesArray = images;
    [self.scrollView addSubview:cycleView2];
    _cycleView2 = cycleView2;
    
    /// 样式二
    YXCycleScrollView *cycleView3 = [[YXCycleScrollView alloc] initWithFrame:CGRectMake(0, 170 + 170, kSCREEN_WIDTH, 150)];
    cycleView3.itemSpacing = 0;
    cycleView3.pageControlStyle = YXCycleScrollViewPageContolStyleAnimated;
    cycleView3.itemZoomScale = 0.85;
    cycleView3.itemSize = CGSizeMake(kSCREEN_WIDTH - 80, cycleView2.frame.size.height);
    cycleView3.imagesArray = images;
    [self.scrollView addSubview:cycleView3];
    _cycleView3 = cycleView3;

    /// 自定义样式 一定要设置代理
    _cycleView4 = [[YXCycleScrollView alloc] initWithFrame:CGRectMake(0, 170 * 3, kSCREEN_WIDTH, 150)];
    _cycleView4.pageControlStyle = YXCycleScrollViewPageContolStyleAnimated;
    _cycleView4.pageControlAliment = YXCycleScrollViewPageContolAlimentRight;
    _cycleView4.imagesArray = images;
    _cycleView4.delegate = self;
    [self.scrollView addSubview:_cycleView4];

```




