# SpringFloatingActionMenu
A menu layout view with makovkastar's `FloatingActionButton`, which means you still can use the features of FAB 
like auto hide while scrolling.

这是一个makovkastar的`FloatingActionButton`基础上的控件,主要效果是点击FAB会弹出菜单,并有动画效果.所以FAB的所有特性都能用,比如当列表滚动自动隐藏等.

# Screenshot 截图
<img src="https://raw.githubusercontent.com/tiancaiCC/SpringFloatingActionMenu/master/art/demo.gif" loop=infinite alt="animation gif" style="width:388;height:690">

<!--![Demo gif](https://raw.githubusercontent.com/tiancaiCC/SpringFloatingActionMenu/master/art/demo.gif)-->

Sample App [download](http://fir.im/wahf)

示例App[下载](http://fir.im/wahf)

<img src="https://raw.githubusercontent.com/tiancaiCC/SpringFloatingActionMenu/master/art/qr.png" alt="qr">


# Usage 用法

Add the dependency to your `build.gradle`.

在`build.gradle`添加依赖
```
dependencies {
   // note v0.0.2 is still uploading
    compile 'com.tiancaicc.springfloatingactionmenu:library:0.0.1'
}
```

setup in Activity `onCreate`method

在`onCreate`方法中设置
```java
       //create your own FAB
       /必须手动创建FAB, 并设置属性
        final FloatingActionButton fab = new FloatingActionButton(this);
        fab.setType(FloatingActionButton.TYPE_NORMAL);
        fab.setImageResource(icon);
        fab.setColorPressedResId(R.color.colorPrimary);
        fab.setColorNormalResId(R.color.fab);
        fab.setColorRippleResId(R.color.text_color);
        fab.setShadow(true);
        
        new SpringFloatingActionMenu.Builder(this)
                .fab(fab)
                //add menu item via addMenuItem(bgColor,icon,label,label color,onClickListener)
                //添加菜单按钮参数依次是背景颜色,图标,标签,标签的颜色,点击事件
                .addMenuItem(R.color.photo, R.mipmap.ic_messaging_posttype_photo, "Photo", R.color.text_color,this)
                .addMenuItem(R.color.chat, R.mipmap.ic_messaging_posttype_chat, "Chat", R.color.text_color,this)
                .addMenuItem(R.color.quote, R.mipmap.ic_messaging_posttype_quote, "Quote", R.color.text_color,this)
                .addMenuItem(R.color.link, R.mipmap.ic_messaging_posttype_link, "Link", R.color.text_color,this)
                .addMenuItem(R.color.audio, R.mipmap.ic_messaging_posttype_audio, "Audio", R.color.text_color,this)
                .addMenuItem(R.color.text, R.mipmap.ic_messaging_posttype_text, "Text", R.color.text_color,this)
                .addMenuItem(R.color.video, R.mipmap.ic_messaging_posttype_video, "Video", R.color.text_color,this)
                //you can choose menu layout animation
                //设置动画类型
                .animationType(SpringFloatingActionMenu.ANIMATION_TYPE_TUMBLR)
                //setup reveal color while the menu opening
                //设置reveal效果的颜色
                .revealColor(R.color.colorPrimary)
                //set FAB location, only support bottom center and bottom right
                //设置FAB的位置,只支持底部居中和右下角的位置
                .gravity(Gravity.RIGHT | Gravity.BOTTOM)
                .onMenuActionListner(new OnMenuActionListener() {
                    @Override
                    public void onMenuOpen() {
                        //set FAB icon when the menu opened
                        //设置FAB的icon当菜单打开的时候
                        fab.setImageResource(icon_closed);
                    }

                    @Override
                    public void onMenuClose() {
                        //set back FAB icon when the menu closed
                        //设置回FAB的图标当菜单关闭的时候
                        fab.setImageResource(icon_opend);
                    }
                })
                .build();
```
Note you should include `toolbar` in your layout xml manually and not use `theme style` or you will find the `reveal` effect not cover the whole screen.

注意不能使用系统提供的主题的`toolbar`,不然`reveal`效果就不会覆盖全屏,应该手动在xml中添加toolbar.


For more usage, you can check out the example.

更多的用法可以参考example.

# 实现原理

[实现原理](http://blog.idropphone.com/2016/03/09/基于FloatingActionButton的一个炫酷菜单控件/)

# Dependencies 依赖

* [rebound](http://facebook.github.io/rebound/)
* [backboard](https://github.com/tumblr/Backboard)
* [FloatingActionButton](https://github.com/makovkastar/FloatingActionButton)
* [SystemBarTint](https://github.com/jgilfelt/SystemBarTint)

# UPDATE LOG

## version 0.0.2
1.Avoid clicks on views behind the menu when is open. Thanks to [@amanzan](https://github.com/amanzan)
2.Fix bug when menu is invisible and still hold the touch event. Thanks to [@brucetoo](https://github.com/brucetoo)
3.Fix bug when MenuItemView is not visible,it's onClick event still can work. Thanks to [@brucetoo](https://github.com/brucetoo)
4.Add support to disable FAB movement
5.Fix: In Last Collapsing animation of menu leaves traces of menu items on screen
6.Fix animation unstable caused by FAB get clicked too fast

# LICENSE

```
Copyright (C) 2016 tiancaiCC

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```