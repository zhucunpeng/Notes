swiper具体使用操作官方API  http://www.swiper.com.cn/api/index.html

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Swiper demo</title>
    <!-- Link Swiper's CSS -->
    <link rel="stylesheet" href="../dist/css/swiper.min.css">

    <!-- Demo styles -->
    <style>
    body {
        background: #eee;
        font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
        font-size: 14px;
        color:#000;
        margin: 0;
        padding: 0;
    }
    .swiper-container {
       width: 500px;
       height: 300px;
       margin: 20px auto;
   } 
    .swiper-slide {
        text-align: center;
        font-size: 18px;
        background: #fff;
        
        /* Center slide text vertically */
        display: -webkit-box;
        display: -ms-flexbox;
        display: -webkit-flex;
        display: flex;
        -webkit-box-pack: center;
        -ms-flex-pack: center;
        -webkit-justify-content: center;
        justify-content: center;
        -webkit-box-align: center;
        -ms-flex-align: center;
        -webkit-align-items: center;
        align-items: center;
    }
    </style>
</head>
<body>
    <!-- Swiper -->
    <div class="swiper-container">
        <div class="swiper-wrapper">
            <div class="swiper-slide">Slide 1</div>
            <div class="swiper-slide">Slide 2</div>
            <div class="swiper-slide">Slide 3</div>
            <div class="swiper-slide">Slide 4</div>
            <div class="swiper-slide">Slide 5</div>
            <div class="swiper-slide">Slide 6</div>
            <div class="swiper-slide">Slide 7</div>
            <div class="swiper-slide">Slide 8</div>
            <div class="swiper-slide">Slide 9</div>
            <div class="swiper-slide">Slide 10</div>
        </div>
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
        <div class="swiper-pagination"></div>
        <div class="swiper-scrollbar"></div>
    </div>

    <!-- Swiper JS -->
    <script src="../dist/js/swiper.min.js"></script>

    <!-- Initialize Swiper -->
    <script>
    var swiper = new Swiper('.swiper-container', {
        autoplay: 1000,//可选选项，自动滑动
        initialSlide :2,//设定初始化时slide的索引。类型：number默认：0举例： 2
        // direction : 'vertical',//Slides的滑动方向，可设置水平(horizontal)或垂直(vertical)。类型：string默认：horizontal举例： vertical
        speed:300,//滑动速度，即slider自动滑动开始到结束的时间（单位ms），也是触摸滑动时释放至贴合的时间。类型：number默认：300举例： 1000
        autoplayDisableOnInteraction : false,//用户操作swiper之后，是否禁止autoplay。默认为true：停止。如果设置为false，用户操作swiper之后自动切换不会停止，每次都会重新启动autoplay。操作包括触碰，拖动，点击pagination等。
        autoplayStopOnLast : true,//默认：false,如果设置为true，当切换到最后一个slide时停止自动切换。（loop模式下无效）
        grabCursor : true,//默认：false,设置为true时，鼠标覆盖Swiper时指针会变成手掌形状，拖动时指针会变成抓手形状。（根据浏览器形状有所不同）
        setWrapperSize :true,//默认：false,Swiper从3.0开始使用flexbox布局(display: flex)，开启这个设定会在Wrapper上添加等于slides相加的宽高，在对flexbox布局的支持不是很好的浏览器中可能需要用到。审查元素查看Wrapper的style
        virtualTranslate : true,//默认：false,虚拟位移。当你启用这个参数，Swiper除了不会移动外其他的都像平时一样运行，仅仅是不会在Wrapper上设置位移。当你想自定义一些slide切换效果时可以用。启用这个选项时onSlideChange和onTransition事件失效。我们只是在活动块的文字上加了点动画，slide并没有移动。
        nextButton: '.swiper-button-next',
        prevButton: '.swiper-button-prev',
        pagination : '.swiper-pagination',
        a11y: true,
        prevSlideMessage: 'Previous slide',
        nextSlideMessage: 'Next slide',
        firstSlideMessage: 'This is the first slide',
        lastSlideMessage: 'This is the last slide',
        paginationBulletMessage:'Go to slide {{index}}',
        /*默认：false,辅助，无障碍阅读。开启本参数为屏幕阅读器添加语音提示等信息，方便视觉障碍者。基于ARIA标准。
        prevSlideMessage    默认：'Previous slide'  在屏幕阅读器为上一页按钮添加信息。
        nextSlideMessage    默认： 'Next slide'   在屏幕阅读器为下一页按钮添加信息。
        firstSlideMessage   默认： 'This is the first slide'  在屏幕阅读器当处于第一个slide为上一页按钮添加信息。
        lastSlideMessage    默认： 'This is the last slide'  在屏幕阅读器当处于最后一个slide为下一页按钮添加信息。
        paginationBulletMessage  默认：'Go to slide {{index}}'在屏幕阅读器为分页器小点添加信息。*/
        roundLengths : true,//默认：false,设定为true将slide的宽和高取整(四舍五入)以防止某些分辨率的屏幕上文字或边界(border)模糊。例如在1440宽度设备上，当你设定slide宽为76%时，则计算出来结果为1094.4，开启后宽度取整数1094。
        slidesPerView: 4,
        spaceBetween: 40,
        breakpoints: { 
            //当宽度小于等于320
            320: {
              slidesPerView: 1,
              spaceBetweenSlides: 10
            },
           //当宽度小于等于480
            480: { 
              slidesPerView: 2,
              spaceBetweenSlides: 20
            },
            //当宽度小于等于640
            640: {
              slidesPerView: 3,
              spaceBetweenSlides: 30
            }
        },
        //断点设定：根据屏幕宽度设置某参数为不同的值，类似于响应式布局的media screen。只有部分不需要变换布局方式和逻辑结构的参数支持断点设定，如slidesPerView、slidesPerGroup、 spaceBetween，而像slidesPerColumn、loop、direction、effect等则无效。
        autoHeight: true, //默认：false,自动高度。设置为true时，wrapper和container会随着当前slide的高度而发生变化。
        freeMode : true,//默认为false，普通模式：slide滑动时只滑动一格，并自动贴合wrapper，设置为true则变为free模式，slide会根据惯性滑动且不会贴合。
        freeMode : true,
        freeModeMomentum : false,//默认：true,free模式动量。free模式下，若设置为false则关闭动量，释放slide之后立即停止不会滑动。
        slidesPerView : 3,
        centeredSlides : true,//默认：false,设定为true时，活动块会居中，而不是默认状态下的居左。默认第一块居左，设置为true后居中
        slidesPerView : 2,//默认：1,设置slider容器能够同时显示的slides数量(carousel模式)。可以设置为number或者 'auto'则自动根据slides的宽度来设定数量。loop模式下如果设置为'auto'还需要设置另外一个参数loopedSlides。
        slidesPerView : 3,
        slidesPerGroup : 3,//默认：1,在carousel mode下定义slides的数量多少为一组。

        slidesPerView : 3,
        spaceBetween : 20,//默认：0,slide之间的距离（单位px）

        slidesPerColumn : 2,//默认：1,多行布局里面每列的slide数量。

        slidesPerColumn : 2,
        slidesPerColumnFill : 'row',//默认：column,多行布局中以什么形式填充：
            /*'column'（列）
            1   3   5
            2   4   6
            'row'（行）。
            1   2   3
            4   5   6*/
        slidesOffsetBefore : 100,//默认：0,设定slide与左边框的预设偏移量（单位px）。
        slidesOffsetAfter : 100,//默认：0,设定slide与右边框的预设偏移量（单位px）。

        effect : 'fade',//fade"（淡入）切换的效果
        effect : 'cube',//"cube"（方块）
        effect : 'coverflow',//"coverflow"（3d流）
        slidesPerView: 3,
        centeredSlides: true,
        effect : 'flip',//"flip"（3d翻转）

        preventClicks : false,//默认：true,当swiper在触摸时阻止默认事件（preventDefault），用于防止触摸时触发链接跳转。设置为false，因此触摸时链接跳转了。

        preventLinksPropagation : false,//默认：true,阻止click冒泡。拖动Swiper时阻止click事件。

        slideToClickedSlide:true,//默认：false,设置为true则点击slide会过渡到这个slide。

        pagination : '.swiper-pagination',//默认：null,分页器容器的css选择器或HTML标签。分页器等组件可以置于container之外，不同Swiper的组件应该有所区分，如#pagination1，#pagination2。

        pagination : '.swiper-pagination',
        paginationType : 'fraction',//默认：bullets,分页器样式类型，可选‘bullets’  圆点（默认） ‘fraction’  分式   ‘progress’  进度条  ‘custom’ 自定义
        paginationClickable :true,//默认：false,此参数设置为true时，点击分页器的指示点分页器会控制Swiper切换。

        paginationHide :true,//默认：false,默认分页器会一直显示。这个选项设置为true时点击Swiper会隐藏/显示分页器。
        paginationElement : 'li',//默认：span举例：li 设定分页器指示器（小点）的HTML标签。

        pagination: '.swiper-pagination',
        paginationClickable: true,
        paginationBulletRender: function (swiper, index, className) {
            return '<span class="' + className + '">' + (index + 1) + '</span>';
        },//默认：null  渲染分页器小点。这个参数允许完全自定义分页器的指示点。接受指示点索引和指示点类名作为参数。
        pagination: '.swiper-pagination',
        paginationType : 'fraction',
        paginationFractionRender: function (swiper, currentClassName, totalClassName) {
            return '<span class="' + currentClassName + '"></span>' +
             ' of ' +
             '<span class="' + totalClassName + '"></span>';
        },

        scrollbar:'.swiper-scrollbar',//默认：null举例： .swiper-scrollbar  Scrollbar容器的css选择器或HTML元素。
        scrollbarHide:false,//滚动条是否自动隐藏。默认：true会自动隐藏。
        scrollbarDraggable : true ,//默认：false 该参数设置为true时允许拖动滚动条。
        scrollbarSnapOnRelease : true ,//默认：false 如果设置为true，释放滚动条时slide自动贴合。
        keyboardControl : true,//默认：false 是否开启键盘控制Swiper切换。设置为true时，能使用键盘方向键控制slide滑动。因为开启了这个选项，现在键盘上的 < 和 > 可以控制Swiper
        mousewheelControl : true,//默认：false 是否开启鼠标控制Swiper切换。设置为true时，能使用鼠标滚轮控制slide滑动。
        direction:'vertical',
        mousewheelForceToAxis : true,//默认：false 当值为true让鼠标滚轮固定于轴向。当水平mode时的鼠标滚轮只有水平滚动才会起效，当垂直mode时的鼠标滚轮只有垂直滚动才会起效。普通家用鼠标只有垂直方向的滚动。
        mousewheelReleaseOnEdges : true,//默认：false 如果开启这个参数，当Swiper处于边缘位置时（第一个或最后一个slide），Swiper释放鼠标滚轮事件，鼠标可以控制页面滚动。
        mousewheelInvert : true,//默认：false 这个参数会使鼠标滚轮控制方向反转。
        mousewheelSensitivity : 2,//默认：1 鼠标滚轮的灵敏度，值越大鼠标滚轮滚动时swiper位移越大。
        loop : true,//默认：false 设置为true 则开启loop模式。loop模式：会在原本slide前后复制若干个slide并在合适的时候切换，让Swiper看起来是循环的。 loop模式在与free模式同用时会产生抖动，因为free模式下没有复制slide的时间点。
        zoom : true,//默认：false 焦距功能：双击slide会放大，并且在手机端可双指触摸缩放。需要在slide中增加类名swiper-zoom-container，结构如下：<div class="swiper-slide"> <div class="swiper-zoom-container"> <img src="path/to/image"> </div> </div>
        zoomMax :5,//默认：3 最大缩放焦距（放大倍率）设置为更大的值后，图片被允许放得更大了

        zoomMin :2,//默认：1 最小缩放焦距（缩小倍率）。
        zoomToggle :false,//默认：true 是否允许双击缩放。设置为false，不允许双击缩放，只允许手机端触摸缩放。
        

    });
    </script>

</body>
</html>

```
