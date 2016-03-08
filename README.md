# SpringFloatingActionMenu
A menu layout with makovkastar's `FloatingActionButton`.

# Screenshot
<img src="https://raw.githubusercontent.com/tiancaiCC/SpringFloatingActionMenu/master/art/demo.gif" alt="animation gif" style="width:388;height:690">

<!--![Demo gif](https://raw.githubusercontent.com/tiancaiCC/SpringFloatingActionMenu/master/art/demo.gif)-->

# Usage

Add the dependency to your `build.gradle`.

```
dependencies {
    //still Waiting for approval
}
```

setup in Activity `onCreate`method
```java
       //create your own FAB
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
                .addMenuItem(R.color.photo, R.mipmap.ic_messaging_posttype_photo, "Photo", R.color.text_color,this)
                .addMenuItem(R.color.chat, R.mipmap.ic_messaging_posttype_chat, "Chat", R.color.text_color,this)
                .addMenuItem(R.color.quote, R.mipmap.ic_messaging_posttype_quote, "Quote", R.color.text_color,this)
                .addMenuItem(R.color.link, R.mipmap.ic_messaging_posttype_link, "Link", R.color.text_color,this)
                .addMenuItem(R.color.audio, R.mipmap.ic_messaging_posttype_audio, "Audio", R.color.text_color,this)
                .addMenuItem(R.color.text, R.mipmap.ic_messaging_posttype_text, "Text", R.color.text_color,this)
                .addMenuItem(R.color.video, R.mipmap.ic_messaging_posttype_video, "Video", R.color.text_color,this)
                //you can choose menu layout animation
                .animationType(SpringFloatingActionMenu.ANIMATION_TYPE_TUMBLR)
                //setup reveal color while the menu opening
                .revealColor(R.color.colorPrimary)
                //set FAB location
                .gravity(Gravity.RIGHT | Gravity.BOTTOM)
                .onMenuActionListner(new OnMenuActionListener() {
                    @Override
                    public void onMenuOpen() {
                        //set FAB icon when the menu opened
                        fab.setImageResource(icon_opend);
                    }

                    @Override
                    public void onMenuClose() {
                        //set back FAB icon when the menu closed
                        fab.setImageResource(icon_opend);
                    }
                })
                .build();
```
For more usage, you can check out the example project.

## Dependencies

* [rebound](http://facebook.github.io/rebound/)
* [backboard](https://github.com/tumblr/Backboard)
* [FloatingActionButton](https://github.com/makovkastar/FloatingActionButton)
* [SystemBarTint](https://github.com/jgilfelt/SystemBarTint)


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