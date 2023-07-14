# pika_lvgl 模块 API 文档

## API

``` python
def __init__():...
```

``` python
def __del__():...
```

### class EVENT:
``` python
def __init__(self):...
```

### class ALIGN:
``` python
def __init__(self):...
```

### class PALETTE:
``` python
def __init__(self):...
```

### class OPA:
``` python
def __init__(self):...
```

### class ANIM:
``` python
def __init__(self):...
```

### class STATE:
``` python
def __init__(self):...
```

### class TEXT_DECOR:
``` python
def __init__(self):...
```

### class lv_event:
``` python
def get_code(self)->int:...
```

``` python
def get_target(self)->lv_obj:...
```

### class lv_color_t:
``` python
def lv_color_hex(hex:int64)->lv_color_t:...
```

### class lv_timer_t:
``` python
def set_period(period:int):...
```

``` python
def set_cb(cb:any):...
```

``` python
def _del(self):...
```

``` python
def palette_lighten(p:int,lvl:int)->lv_color_t:...
```

``` python
def palette_main(p:int)->lv_color_t:...
```

### class style_t:
``` python
def __init__(self):...
```

``` python
def init(self):...
```

``` python
def set_width(self,value:int):...
```

``` python
def set_min_width(self,value:int):...
```

``` python
def set_max_width(self,value:int):...
```

``` python
def set_height(self,value:int):...
```

``` python
def set_min_height(self,value:int):...
```

``` python
def set_max_height(self,value:int):...
```

``` python
def set_x(self,value:int):...
```

``` python
def set_y(self,value:int):...
```

``` python
def set_align(self,value:int):...
```

``` python
def set_transform_width(self,value:int):...
```

``` python
def set_transform_height(self,value:int):...
```

``` python
def set_translate_x(self,value:int):...
```

``` python
def set_translate_y(self,value:int):...
```

``` python
def set_transform_zoom(self,value:int):...
```

``` python
def set_transform_angle(self,value:int):...
```

``` python
def set_transform_pivot_x(self,value:int):...
```

``` python
def set_transform_pivot_y(self,value:int):...
```

``` python
def set_pad_top(self,value:int):...
```

``` python
def set_pad_bottom(self,value:int):...
```

``` python
def set_pad_left(self,value:int):...
```

``` python
def set_pad_right(self,value:int):...
```

``` python
def set_pad_row(self,value:int):...
```

``` python
def set_pad_column(self,value:int):...
```

``` python
def set_bg_color(self,value:lv_color_t):...
```

``` python
def set_bg_opa(self,value:int):...
```

``` python
def set_bg_grad_color(self,value:lv_color_t):...
```

``` python
def set_bg_grad_dir(self,value:int):...
```

``` python
def set_bg_main_stop(self,value:int):...
```

``` python
def set_bg_grad_stop(self,value:int):...
```

``` python
def set_bg_dither_mode(self,value:int):...
```

``` python
def set_bg_img_src(self,value:bytes):...
```

``` python
def set_bg_img_opa(self,value:int):...
```

``` python
def set_bg_img_recolor(self,value:lv_color_t):...
```

``` python
def set_bg_img_recolor_opa(self,value:int):...
```

``` python
def set_bg_img_tiled(self,value:int):...
```

``` python
def set_border_color(self,value:lv_color_t):...
```

``` python
def set_border_opa(self,value:int):...
```

``` python
def set_border_width(self,value:int):...
```

``` python
def set_border_side(self,value:int):...
```

``` python
def set_border_post(self,value:int):...
```

``` python
def set_outline_width(self,value:int):...
```

``` python
def set_outline_color(self,value:lv_color_t):...
```

``` python
def set_outline_opa(self,value:int):...
```

``` python
def set_outline_pad(self,value:int):...
```

``` python
def set_shadow_width(self,value:int):...
```

``` python
def set_shadow_ofs_x(self,value:int):...
```

``` python
def set_shadow_ofs_y(self,value:int):...
```

``` python
def set_shadow_spread(self,value:int):...
```

``` python
def set_shadow_color(self,value:lv_color_t):...
```

``` python
def set_shadow_opa(self,value:int):...
```

``` python
def set_img_opa(self,value:int):...
```

``` python
def set_img_recolor(self,value:lv_color_t):...
```

``` python
def set_img_recolor_opa(self,value:int):...
```

``` python
def set_line_width(self,value:int):...
```

``` python
def set_line_dash_width(self,value:int):...
```

``` python
def set_line_dash_gap(self,value:int):...
```

``` python
def set_line_rounded(self,value:int):...
```

``` python
def set_line_color(self,value:lv_color_t):...
```

``` python
def set_line_opa(self,value:int):...
```

``` python
def set_arc_width(self,value:int):...
```

``` python
def set_arc_rounded(self,value:int):...
```

``` python
def set_arc_color(self,value:lv_color_t):...
```

``` python
def set_arc_opa(self,value:int):...
```

``` python
def set_arc_img_src(self,value:bytes):...
```

``` python
def set_text_color(self,value:lv_color_t):...
```

``` python
def set_text_opa(self,value:int):...
```

``` python
def set_text_letter_space(self,value:int):...
```

``` python
def set_text_line_space(self,value:int):...
```

``` python
def set_text_decor(self,value:int):...
```

``` python
def set_text_align(self,value:int):...
```

``` python
def set_radius(self,value:int):...
```

``` python
def set_clip_corner(self,value:int):...
```

``` python
def set_opa(self,value:int):...
```

``` python
def set_color_filter_opa(self,value:int):...
```

``` python
def set_anim_time(self,value:int):...
```

``` python
def set_anim_speed(self,value:int):...
```

``` python
def set_blend_mode(self,value:int):...
```

``` python
def set_layout(self,value:int):...
```

``` python
def set_base_dir(self,value:int):...
```

``` python
def reset(self):...
```

``` python
def register_prop(self,flag:int)->int:...
```

``` python
def get_num_custom_props(self)->int:...
```

``` python
def remove_prop(self,prop:int)->int:...
```

``` python
def is_empty(self)->int:...
```

``` python
def set_size(self,value:int):...
```

``` python
def set_pad_all(self,value:int):...
```

``` python
def set_pad_hor(self,value:int):...
```

``` python
def set_pad_ver(self,value:int):...
```

``` python
def set_pad_gap(self,value:int):...
```

``` python
def prop_has_flag(self,prop:int,flag:int)->int:...
```

``` python
def set_flex_flow(self,value:int):...
```

``` python
def set_flex_main_place(self,value:int):...
```

``` python
def set_flex_cross_place(self,value:int):...
```

``` python
def set_flex_track_place(self,value:int):...
```

``` python
def set_flex_grow(self,value:int):...
```

### class LAYOUT_FLEX:
``` python
def __init__(self):...
```

### class SIZE:
``` python
def __init__(self):...
```

### class flag_t:
``` python
def __init__(self):...
```

### class FLEX_FLOW:
``` python
def __init__(self):...
```

### class lv_obj:
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def add_state(self,state:int):...
```

``` python
def add_flag(self,flag:int):...
```

``` python
def clear_flag(self,flag:int):...
```

``` python
def add_event_cb(self,event_cb:any,filter:int,user_data:pointer):...
```

``` python
def add_style(self,style:style_t,selector:int):...
```

``` python
def set_pos(self,x:int,y:int):...
```

``` python
def set_x(self,x:int):...
```

``` python
def set_y(self,y:int):...
```

``` python
def set_size(self,w:int,h:int):...
```

``` python
def refr_size(self)->int:...
```

``` python
def set_width(self,w:int):...
```

``` python
def set_height(self,h:int):...
```

``` python
def set_content_width(self,w:int):...
```

``` python
def set_content_height(self,h:int):...
```

``` python
def set_layout(self,layout:int):...
```

``` python
def is_layout_positioned(self)->int:...
```

``` python
def mark_layout_as_dirty(self):...
```

``` python
def update_layout(self):...
```

``` python
def set_align(self,align:int):...
```

``` python
def align(self,align:int,x_ofs:int,y_ofs:int):...
```

``` python
def align_to(self,base:lv_obj,align:int,x_ofs:int,y_ofs:int):...
```

``` python
def center(self):...
```

``` python
def get_x(self)->int:...
```

``` python
def get_x2(self)->int:...
```

``` python
def get_y(self)->int:...
```

``` python
def get_y2(self)->int:...
```

``` python
def get_x_aligned(self)->int:...
```

``` python
def get_y_aligned(self)->int:...
```

``` python
def get_width(self)->int:...
```

``` python
def get_height(self)->int:...
```

``` python
def get_content_width(self)->int:...
```

``` python
def get_content_height(self)->int:...
```

``` python
def get_self_width(self)->int:...
```

``` python
def get_self_height(self)->int:...
```

``` python
def refresh_self_size(self)->int:...
```

``` python
def refr_pos(self):...
```

``` python
def move_to(self,x:int,y:int):...
```

``` python
def move_children_by(self,x_diff:int,y_diff:int,ignore_floating:int):...
```

``` python
def transform_point(self,p:point_t,recursive:int,inv:int):...
```

``` python
def invalidate(self):...
```

``` python
def is_visible(self)->int:...
```

``` python
def set_ext_click_area(self,size:int):...
```

``` python
def set_style_size(self,value:int,selector:int):...
```

``` python
def hit_test(self,point:point_t)->int:...
```

``` python
def set_flex_flow(self,flow:int):...
```

``` python
def set_flex_grow(self,value:int):...
```

``` python
def set_flex_align(self,main_place:int,cross_place:int,align:int):...
```

``` python
def set_id(self,id:str):...
```

``` python
def get_id(self)->str:...
```

``` python
def clean(self):...
```

``` python
def del_(self):...
```

### class indev_t:
``` python
def get_vect(self,point:point_t):...
```

### class FLEX_ALIGN:
``` python
def __init__(self):...
```

### class obj(lv_obj):
``` python
def __init__(self,*parent):...
```

``` python
def indev_get_act()->indev_t:...
```

### class point_t:
``` python
def __init__(self):...
```

### class arc(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_start_angle(self,start:int):...
```

``` python
def set_end_angle(self,angle:int):...
```

``` python
def set_angles(self,start:int,end:int):...
```

``` python
def set_bg_start_angle(self,start:int):...
```

``` python
def set_bg_end_angle(self,angle:int):...
```

``` python
def set_bg_angles(self,start:int,end:int):...
```

``` python
def set_rotation(self,rotation:int):...
```

``` python
def set_mode(self,mode:int):...
```

``` python
def set_value(self,value:int):...
```

``` python
def set_range(self,min:int,max:int):...
```

``` python
def set_change_rate(self,rate:int):...
```

``` python
def get_angle_start(self)->int:...
```

``` python
def get_angle_end(self)->int:...
```

``` python
def get_bg_angle_start(self)->int:...
```

``` python
def get_bg_angle_end(self)->int:...
```

``` python
def get_value(self)->int:...
```

``` python
def get_min_value(self)->int:...
```

``` python
def get_max_value(self)->int:...
```

``` python
def get_mode(self)->int:...
```

### class bar(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_value(self,value:int,anim:int):...
```

``` python
def set_start_value(self,start_value:int,anim:int):...
```

``` python
def set_range(self,min:int,max:int):...
```

``` python
def set_mode(self,mode:int):...
```

``` python
def get_value(self)->int:...
```

``` python
def get_start_value(self)->int:...
```

``` python
def get_min_value(self)->int:...
```

``` python
def get_max_value(self)->int:...
```

``` python
def get_mode(self)->int:...
```

### class btn(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

### class checkbox(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_text(self,txt:str):...
```

``` python
def set_text_static(self,txt:str):...
```

``` python
def get_text(self)->str:...
```

### class dropdown(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_text(self,txt:str):...
```

``` python
def set_options(self,options:str):...
```

``` python
def add_option(self,option:str,pos:int):...
```

``` python
def clear_options(self):...
```

``` python
def set_selected(self,sel_opt:int):...
```

``` python
def set_dir(self,dir:int):...
```

``` python
def set_symbol(self,symbol:str):...
```

``` python
def set_selected_hightlight(self,en:int):...
```

``` python
def get_text(self)->str:...
```

``` python
def get_options(self)->str:...
```

``` python
def get_selected(self)->int:...
```

``` python
def get_option_cnt(self)->int:...
```

``` python
def get_selected_str(self)->str:...
```

``` python
def get_option_index(self,option:str)->int:...
```

``` python
def get_symbol(self)->str:...
```

``` python
def get_selected_highlight(self)->int:...
```

``` python
def get_dir(self)->int:...
```

``` python
def open(self):...
```

``` python
def close(self):...
```

``` python
def is_open(self)->int:...
```

### class label(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_text(self,txt:str):...
```

``` python
def set_long_mode(self,mode:int):...
```

``` python
def set_recolor(self,en:int):...
```

``` python
def set_style_text_align(self,value:int,selector:int):...
```

### class roller(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_options(self,options:str,mode:int):...
```

``` python
def set_visible_row_count(self,row_cnt:int):...
```

### class slider(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

### class switch(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

### class table(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_cell_value(self,row:int,col:int,txt:str):...
```

### class img_dsc_t:
``` python
def __init__(self,dsc_dict:dict):...
```

### class cf_t:
``` python
def __init__(self):...
```

### class img(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_src(self,src:img_dsc_t):...
```

``` python
def set_offset_x(self,x:int):...
```

``` python
def set_offset_y(self,y:int):...
```

``` python
def set_angle(self,angle:int):...
```

``` python
def set_pivot(self,x:int,y:int):...
```

``` python
def set_zoom(self,zoom:int):...
```

``` python
def set_antialias(self,antialias:int):...
```

``` python
def set_size_mode(self,mode:int):...
```

``` python
def get_src(self)->img_dsc_t:...
```

``` python
def get_offset_x(self)->int:...
```

``` python
def get_offset_y(self)->int:...
```

``` python
def get_angle(self)->int:...
```

``` python
def get_zoom(self)->int:...
```

``` python
def get_antialias(self)->int:...
```

``` python
def get_size_mode(self)->int:...
```

### class textarea(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_one_line(en:int):...
```

### class canvas(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_buffer(self,buf:any,w:int,h:int,cf:int):...
```

``` python
def set_px(self,x:int,y:int,color:lv_color_t,opa:int):...
```

``` python
def set_palette(self,id:int,c:lv_color_t):...
```

``` python
def get_px(self,x:int,y:int,color:lv_color_t,opa:int):...
```

``` python
def get_img(self)->img_dsc_t:...
```

``` python
def copy_buf(self,to_copy:bytes,x:int,y:int,w:int,h:int):...
```

``` python
def transform(self,img:img_dsc_t,angle:int,zoom:int,offset_x:int,offset_y:int,pivot_x:int,pivot_y:int,antialias:bool):...
```

``` python
def fill_bg(self,color:lv_color_t,opa:int):...
```

### class chart_series_t:
### class chart(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

``` python
def set_point_count(self,cnt:int):...
```

``` python
def set_range(self,axis:int,min:int,max:int):...
```

``` python
def set_zoom_x(self,zoom_x:int):...
```

``` python
def set_zoom_y(self,zoom_y:int):...
```

``` python
def add_series(self,color:lv_color_t,axis:int)->chart_series_t:...
```

``` python
def get_series_next(self,ser:chart_series_t)->chart_series_t:...
```

``` python
def set_ext_y_array(self,ser:chart_series_t,array:any):...
```

``` python
def refresh(self):...
```

``` python
def scr_act()->lv_obj:...
```

``` python
def pct(x:int)->int:...
```

``` python
def timer_create_basic()->lv_timer_t:...
```



## Examples

### lv_table1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

table = lv.table(lv.scr_act())

# Fill the first column
table.set_cell_value(0, 0, "Name")
table.set_cell_value(1, 0, "Apple")
table.set_cell_value(2, 0, "Banana")
table.set_cell_value(3, 0, "Lemon")
table.set_cell_value(4, 0, "Grape")
table.set_cell_value(5, 0, "Melon")
table.set_cell_value(6, 0, "Peach")
table.set_cell_value(7, 0, "Nuts")

# Fill the second column
table.set_cell_value(0, 1, "Price")
table.set_cell_value(1, 1, "$7")
table.set_cell_value(2, 1, "$4")
table.set_cell_value(3, 1, "$6")
table.set_cell_value(4, 1, "$2")
table.set_cell_value(5, 1, "$5")
table.set_cell_value(6, 1, "$1")
table.set_cell_value(7, 1, "$9")

# Set a smaller height to the table. It'll make it scrollable
table.set_height(200)
table.center()

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_obj2.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

obj = lv.obj(lv.scr_act())
obj.set_size(150, 100)

label = lv.label(obj)
label.set_text("test")
label.center()

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_callback1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()


def event_cb_1(evt):
    print('in evt1')
    print('mem used now: %0.2f kB' % (mem.getNow()))


def event_cb_2(evt):
    print('in evt2')
    print('mem used now: %0.2f kB' % (mem.getNow()))


btn1 = lv.btn(lv.scr_act())
btn1.align(lv.ALIGN.TOP_MID, 0, 10)
btn2 = lv.btn(lv.scr_act())
btn2.align(lv.ALIGN.TOP_MID, 0, 50)
btn1.add_event_cb(event_cb_1, lv.EVENT.CLICKED, 0)
btn2.add_event_cb(event_cb_2, lv.EVENT.CLICKED, 0)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_png.py

```python
import lvgl as lv

f = open('/pikafs/1.png', 'rb')
img_data = f.read()
f.close()  

   
img_dsc = lv.img_dsc_t({
    "data_size": len(img_data),
    "data": img_data,
})

img = lv.img(lv.scr_act())
img.set_zoom(500)
img.align(lv.ALIGN.CENTER, 0, -20)
img.set_src(img_dsc)

```
### lv_btn1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

# create a simple button
btn1 = lv.btn(lv.scr_act())

btn1.align(lv.ALIGN.CENTER,0,-40)
label=lv.label(btn1)
label.set_text("Button")

# create a toggle button
btn2 = lv.btn(lv.scr_act())

btn2.align(lv.ALIGN.CENTER,0,40)
btn2.add_flag(lv.obj.FLAG.CHECKABLE)
btn2.set_height(lv.SIZE.CONTENT)

label=lv.label(btn2)
label.set_text("Toggle")
label.center()

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_arc1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

# Create an Arc
arc = lv.arc(lv.scr_act())
arc.set_end_angle(200)
arc.set_size(150, 150)
arc.center()

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))
#!pika
```
### lv_bar1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

bar1 = lv.bar(lv.scr_act())
bar1.set_size(200, 20)
bar1.center()
bar1.set_value(70, lv.ANIM.OFF)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))
#!pika

```
### lv_label1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

label1 = lv.label(lv.scr_act())
LV_LABEL_LONG_WRAP = 0
label1.set_long_mode(LV_LABEL_LONG_WRAP)      # Break the long lines*/
# Enable re-coloring by commands in the text
label1.set_recolor(True)
label1.set_text("#0000ff Re-color# #ff00ff words# #ff0000 of a# label, \
align the lines to the center and  wrap long text automatically.")
# Set smaller width to make the lines wrap
label1.set_width(150)
label1.set_style_text_align(lv.ALIGN.CENTER, 0)
label1.align(lv.ALIGN.CENTER, 0, -40)

LV_LABEL_LONG_SCROLL_CIRCULAR = 3
label2 = lv.label(lv.scr_act())
label2.set_long_mode(LV_LABEL_LONG_SCROLL_CIRCULAR)  # Circular scroll
label2.set_width(150)
label2.set_text("It is a circularly scrolling text. ")
label2.align(lv.ALIGN.CENTER, 0, 40)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))
#!pika

```
### lv_arc2.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

# Create an Arc
arc = lv.arc(lv.scr_act())
arc.set_bg_angles(0, 360)
arc.set_angles(270, 270)
arc.center()

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_drag.py

```python
#!pika
import pika_lvgl as lv
from PikaStdLib import MemChecker

mem = MemChecker()

def drag_event_handler(e):

    obj = e.get_target()

    indev = lv.indev_get_act()

    vect = lv.point_t()
    indev.get_vect(vect)
    x = obj.get_x() + vect.x
    y = obj.get_y() + vect.y
    obj.set_pos(x, y)
    mem.now()


#
# Make an object dragable.
#

obj = lv.obj(lv.scr_act())
obj.set_size(150, 100)
obj.add_event_cb(drag_event_handler, lv.EVENT.PRESSING, None)

label = lv.label(obj)
label.set_text("Drag me")
label.center()

#!pika
```
### lv_checkbox1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

cb = lv.checkbox(lv.scr_act())
cb.set_text("Apple")
cb.align(lv.ALIGN.TOP_LEFT, 0 ,0)

cb = lv.checkbox(lv.scr_act())
cb.set_text("Banana")
cb.add_state(lv.STATE.CHECKED)
cb.align(lv.ALIGN.TOP_LEFT, 0 ,30)

cb = lv.checkbox(lv.scr_act())
cb.set_text("Lemon")
cb.add_state(lv.STATE.DISABLED)
cb.align(lv.ALIGN.TOP_LEFT, 0 ,60)

cb = lv.checkbox(lv.scr_act())
cb.add_state(lv.STATE.CHECKED | lv.STATE.DISABLED)
cb.set_text("Melon")
cb.align(lv.ALIGN.TOP_LEFT, 0 ,90)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_slider1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

# Create a slider in the center of the display
slider = lv.slider(lv.scr_act())
slider.center()

# Create a label below the slider
slider_label = lv.label(lv.scr_act())
slider_label.set_text("0%")

slider_label.align_to(slider, lv.ALIGN.OUT_BOTTOM_MID, 0, 10)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_obj3.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

obj1 = lv.obj(lv.scr_act())
obj1.set_size(100, 50)
obj1.align(lv.ALIGN.CENTER, -60, -30)

style_shadow = lv.style_t()
style_shadow.init()
style_shadow.set_shadow_width(10)
style_shadow.set_shadow_spread(5)
style_shadow.set_shadow_color(lv.palette_main(lv.PALETTE.BLUE))

obj2 = lv.obj(lv.scr_act())
obj2.add_style(style_shadow, 0)
obj2.align(lv.ALIGN.CENTER, 60, 30)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_textarea1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

ta = lv.textarea(lv.scr_act())
ta.set_one_line(True)
ta.align(lv.ALIGN.TOP_MID, 0, 10)
ta.add_state(lv.STATE.FOCUSED)   # To be sure the cursor is visible

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_list1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

# Create a normal drop down list
dd = lv.dropdown(lv.scr_act())
dd.set_options("Apple\nBanana\nOrange\nCherry\nGrape\
Raspberry\nMelon\nOrange\nLemon\nNuts")

dd.align(lv.ALIGN.TOP_MID, 0, 20)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_style1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

style = lv.style_t()
style.init()

# Set a background color and a radius
style.set_radius(5)
style.set_bg_opa(lv.OPA.COVER)
style.set_bg_color(lv.palette_lighten(lv.PALETTE.GREY, 1))

# Add outline
style.set_outline_width(2)
style.set_outline_color(lv.palette_main(lv.PALETTE.BLUE))
style.set_outline_pad(8)

# Create an object with the new style
obj = lv.obj(lv.scr_act())
obj.add_style(style, 0)
obj.center()

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_obj1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

obj1 = lv.obj(lv.scr_act())
obj1.set_size(100, 50)
obj1.align(lv.ALIGN.CENTER, -60, -30)

obj2 = lv.obj(lv.scr_act())
obj2.align(lv.ALIGN.CENTER, 60, 30)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_roller1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

LV_ROLLER_MODE_INFINITE = 1
roller1 = lv.roller(lv.scr_act())
roller1.set_options("January\nFebruary\nMarch\nApril\
\nMay\nJune\nJuly\nAugust\nSeptember\
\nOctober\nNovember\nDecember", LV_ROLLER_MODE_INFINITE)

roller1.set_visible_row_count(4)
roller1.center()

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
### lv_switch1.py

```python
#!pika
import pika_lvgl as lv
import PikaStdLib
mem = PikaStdLib.MemChecker()

sw = lv.switch(lv.scr_act())
sw.align(lv.ALIGN.TOP_MID, 0, 20)

sw = lv.switch(lv.scr_act())
sw.add_state(lv.STATE.CHECKED)
sw.align(lv.ALIGN.TOP_MID, 0, 50)

sw = lv.switch(lv.scr_act())
sw.add_state(lv.STATE.DISABLED)
sw.align(lv.ALIGN.TOP_MID, 0, 80)

sw = lv.switch(lv.scr_act())
sw.add_state(lv.STATE.CHECKED | lv.STATE.DISABLED)
sw.align(lv.ALIGN.TOP_MID, 0, 110)

print('mem used max: %0.2f kB' % (mem.getMax()))
print('mem used now: %0.2f kB' % (mem.getNow()))

#!pika
```
