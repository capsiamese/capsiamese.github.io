# introduction
[TkReference](https://tcl.tk/man/tcl8.6/TkCmd/contents.htm)

[Tkinter8.5Tutor](https://anzeljg.github.io/rin2/book2/2405/docs/tkinter/index.html)
[TkDocs](https://tkdocs.com/tutorial/intro.html)
[pyguis](https://www.pythonguis.com/tkinter-tutorial/)
[pythonTutorial](https://www.pythontutorial.net/tkinter/)
[TkTutor](https://www.tutorialspoint.com/python/python_gui_programming.htm)
[RealPythonTk](https://realpython.com/python-gui-tkinter/)

# Concept

## Widgets

1. ttk.Frame(root, padding)
2. ttk.Button(root, text, command)
3. ttk.Entry(root, width, textvariable)
4. ttk.Label(root, text)

Frame.winfo_children() 获取所有子组件
widget.configure(kw='') 设置参数
widget.configure() 获取所有参数
widget.configure('') 查询某个参数

widget.winfo_xxx() 获取组件的信息
1. winfo_class 获取某类组件的类标识
2. winfo_children 获取所有直接子组件
3. winfo_parent 获取父组件
4. winfo_toplevel 包含这个组件的顶层窗口
5. winfo_width winfo_height 获取组件的宽高
6. winfo_reqwith winfo_reqheight 获取组件告诉窗口管理器的请求宽高
7. winfo_x winfo_x 获取组件想对父组件的左上角坐标
8. winfo_rootx winfo_rooty 获取组件相对屏幕的坐标
9. winfo_vieweable 判断组件是否可见

### Frame
frame = ttk.Frame(parent, style='Danger.TFrame')
通常所有的风格化组件都有style关键字参数来设置风格
f['padding'] = 5 # All 5
f['padding'] = (5,10) # LR=5 TB=10
f['padding'] = (5,10,20,1) # Left,Top,Right,Bottom

f['borderwidth'] = 2
f['relief'] = 'flat','raised','sunken','solid','ridge','groove' 边界的质感

### Label
label = ttk.Label(parent, text='')
用来展示文本或者图片
label['textvariable'] = StringVar() 可以动态改变文本
img = PhotoImage(file='')
label['image'] = img 展示图片
label['font'] = 'TkDefaultFount'

label可以同时展示文字和图片, 使用`compound`configuration选项

### Button
button = ttk.Button(parent, text='', command=func)
button.state(['disabled']) set disable
button.state(['!disabled']) clear disable
button.instate(['disabled']) true if disabled
button.instate(['!disabled']) true if not disabled
button.instate(['disabled'], cmd) execute cmd if disabled
stateFlags = ['active',disabled,focus,pressed,selected,background,readonly,alternate,invalid]

### Checkbutton
check = ttk.Checkbutton(parent, text='', command=cmd,variable=var,onvalue='',offvalue='')

### Radiobutton
a = ttk.Radiobutton(parent, text='',variable=var, value='')
b = ttk.Radiobutton(parent, text='',variable=var, value='')

### Entry
entry = ttk.Entry(parent,textvariable,show="*",validatecommand)
entry.insert(index,'')
entry.delete(index,'')
entry.trace_add('',cmd) 订阅内容改变事件

### Combobox
cbb = ttk.Combobox(parent, textvariable)
cbb['values'] = ('','','')

### Listbox
Listbox(parent, height, listvariable)
### Scrollbar
ttk.Scrollbar(parent,orient=VERTICAL,command=listbox.yview)
listbox.configure(yscrollcommand=cmd)
### Text
Text(parent, width, height)
### Scale
ttk.Scale(parent,orient=HORIZONTAL,length,from_,to)
### Spinbox
ttk.Spinbox(parent,from_,to,textvariable)
### Progressbar
ttk.Progressbar(parent,orient=HORIZONTAL,length,mode='determinate')


### Misc
ttk.Separator
ttk.Labelframe
ttk.PanedWindow
ttk.Notebook
ttk.Treeview

## GeometryManagement
### Grid
widget.grid(column,row, columnspan, rowspan, sticky, padx, pady)
网格布局中, 每个组件都被赋予了一个行号和列号, span表示占几列/行

widget.columnconfigure(index,weight)
widget.rowconfigure(index,weight)

grid_configure(padx, pady) # 设置组件的内边距

## EventHandling
widget.bind('', command)绑定事件
root.event_generate('<<xxx>>') 虚拟事件

变量
1. StringVar(value=)
2. BooleanVar(value=)
3. IntVar(value=)
4. DoubleVar(value=)

## Menubar
添加菜单栏前需要调用
root.option_add('',FALSE)
win = Toplevel(root)
menubar = Menu(win)
menubar.add_command(label, command)
menubar.add_cascade(menu=,label=)
menubar.add_separator()
win['menu'] = menubar

## Dialog 
`from tkinter import filedialog`
1. filedialog.askopenfilename()
2. filedialog.asksaveasfilename()
3. filedialog.askdirectory()

`from tkinter import messagebox`
1. messagebox.showinfo(message=)
2. messagebox.askyesno(message=,icon=,title=)

## ColorChooser
`from tkinter import colorchooser`
colorchooser.askcolor()


# Canvas
canvas = Canvas(parent,width,height,background)
1. canvas.create_line(x1,y1,x2,y2,fill,width)
2. canvas.create_rectangle(x1,y1,x2,y2,fill,outline)
3. canvas.create_oval
4. canvas.create_polygon
5. canvas.create_arc
6. canvas.create_image
7. canvas.create_text
8. canvas.create_window