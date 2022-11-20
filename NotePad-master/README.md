# NotePad应用功能扩展

### 1.NoteList界面中笔记条目增加时间戳显示

- #### 思路

  （1）修改noteslist_item.xml，加入一个TextView，
  
   （2）修改时间戳类型，修改一下时间戳的格式新建笔记在NotePadProvider中的insert方法，修改笔记在NoteEditor中的updateNote方法
   
   （3）将PROJECTION添加上修改时间，修改NotesList.java中PROJECTION的内容，添加modif字段
   
   
- #### 部分实验代码：

 private static final String[] PROJECTION = new String[] {
            NotePad.Notes._ID, // 0
            NotePad.Notes.COLUMN_NAME_TITLE, // 1
            NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE,//添加修改时间
    };

String[] dataColumns = { NotePad.Notes.COLUMN_NAME_TITLE, NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE }//加入修改时间;
int[] viewIDs = { android.R.id.text1, R.id.text2 }//加入修改时间;


- #### 实验结果如下图：

- ![avatar]([https://i.ibb.co/sVMLz7Y/02-1.png](https://github.com/1814870464/Android/blob/main/%E6%88%AA%E5%9B%BE/sck_1.png))
