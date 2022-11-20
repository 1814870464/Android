# NotePad应用功能扩展

### 1.NoteList界面中笔记条目增加时间戳显示

- #### 思路

  （1）修改noteslist_item.xml，加入一个TextView
  
   （2）修改时间戳类型，修改一下时间戳的格式新建笔记在NotePadProvider中的insert方法，修改笔记在NoteEditor中的updateNote方法
   
   （3）将PROJECTION添加上修改时间，修改NotesList.java中PROJECTION的内容，添加modif字段
   
   
- #### 部分实验代码：
```
 private static final String[] PROJECTION = new String[] {
            NotePad.Notes._ID, // 0           
            NotePad.Notes.COLUMN_NAME_TITLE, // 1            
            NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE,//添加修改时间       
    };
```
```
String[] dataColumns = { NotePad.Notes.COLUMN_NAME_TITLE, NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE }//加入修改时间;
int[] viewIDs = { android.R.id.text1, R.id.text2 }//加入修改时间;
```

- #### 实验结果如下图：

- - ![avatar](https://github.com/1814870464/Android/blob/main/images/sck_1.png)

### 2.NoteList界面添加笔记查询功能

- #### 思路

（1）在list_option_menu.xml里边添加一个搜索图标

 （2）添加menu_search图标的点击选择事件
 
 （3）新建一个NoteSearch的Activity，它的布局文件为note_search.xml
 
 （4）注册NoteSearch
 
 - #### 部分实验代码：
 
 （1）
 ```
 <item    
          android:id="@+id/menu_search"
          android:icon="@android:drawable/ic_search_category_default"
          android:showAsAction="always"
           android:title="search">  
    </item>
```
 （2）
```
 case R.id.menu_search:
 
                Intent intent = new Intent();
                
                intent.setClass(this, NoteSearch.class);
                
                this.startActivity(intent);
                
                return true;
```

- #### 实验结果如下图：
- - ![avatar](https://github.com/1814870464/Android/blob/main/images/sck_2.png)
 
 
 
 ### 3.NoteList  UI美化
 
 （1）给NotesList换个主题，在数据库中增加一个字段“color”用于存放每条笔记的背景颜色
 
 （2）创建数据库表地方添加颜色的字段。
 
 （3）实例化和设置静态对象的块
 
 （4）自定义一个MyCursorAdapter.java，将颜色填充到ListView
 
 （5）在NotesList.java中的PROJECTION添加颜色项，并将SimpleCursorAdapter改为使用MyCursorAdapter
 
  - #### 部分实验代码：
  ```
        public static final String COLUMN_NAME_BACK_COLOR = "color";
        public static final int DEFAULT_COLOR = 0; //white
        public static final int YELLOW_COLOR = 1; //yellow
        public static final int BLUE_COLOR = 2; //blue
        public static final int GREEN_COLOR = 3; //green
        public static final int RED_COLOR = 4; //red
```
 - #### 实验结果如下图：
- - ![avatar](https://github.com/1814870464/Android/blob/main/images/sck_3.png)
 
 
 
 
 
 
