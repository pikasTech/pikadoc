# pika_lvgl 模块 API 文档

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

### class img(lv_obj):
``` python
def __init__(self,parent:lv_obj):...
```

   void lv_img_set_src(lv_obj_t * obj, const void * src);
   void lv_img_set_offset_x(lv_obj_t * obj, lv_coord_t x);
   void lv_img_set_offset_y(lv_obj_t * obj, lv_coord_t y);
   void lv_img_set_angle(lv_obj_t * obj, int16_t angle);
   void lv_img_set_pivot(lv_obj_t * obj, lv_coord_t x, lv_coord_t y);
   void lv_img_set_zoom(lv_obj_t * obj, uint16_t zoom);
   void lv_img_set_antialias(lv_obj_t * obj, bool antialias);
   void lv_img_set_size_mode(lv_obj_t * obj, lv_img_size_mode_t mode);
   const void * lv_img_get_src(lv_obj_t * obj);
   lv_coord_t lv_img_get_offset_x(lv_obj_t * obj);
   lv_coord_t lv_img_get_offset_y(lv_obj_t * obj);
   uint16_t lv_img_get_angle(lv_obj_t * obj);
   void lv_img_get_pivot(lv_obj_t * obj, lv_point_t * pivot);
   uint16_t lv_img_get_zoom(lv_obj_t * obj);
   bool lv_img_get_antialias(lv_obj_t * obj);
   lv_img_size_mode_t lv_img_get_size_mode(lv_obj_t * obj);
   

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

``` python
def scr_act()->lv_obj:...
```

``` python
def pct(x:int)->int:...
```

``` python
def timer_create_basic()->lv_timer_t:...
```

