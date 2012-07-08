---
layout: post
title: Ext xtype罗列
wordpress_id: 369
wordpress_url: http://www.hijava.org/?p=369
date: 2009-05-08 21:09:37.000000000 +08:00
---
<span style="font-family: monospace;">Ext2.0对框架进行了非常大的重构，其中最重要的就是形成了一个结构及层次分明的组件体系，由这些组件形成了Ext的控件，Ext组件是由 Component类定义，每一种组件都有一个指定的xtype属性值，通过该值可以得到一个组件的类型或者是定义一个指定类型的组件。</span>
<div><span style="font-family: monospace;">
组件大致可以分成三大类，即基本组件、工具栏组件、表单及元素组件。
基本组件有：

xtype            Class
-------------    ------------------
box              Ext.BoxComponent  具有边框属性的组件
button           Ext.Button　　按钮
colorpalette     Ext.ColorPalette 调色板
component        Ext.Component　组件
container        Ext.Container　容器
cycle            Ext.CycleButton
dataview         Ext.DataView 数据显示视图
datepicker       Ext.DatePicker 日期选择面板
editor           Ext.Editor　编辑器
editorgrid       Ext.grid.EditorGridPanel 可编辑的表格
grid             Ext.grid.GridPanel 表格
paging           Ext.PagingToolbar 工具栏中的间隔
panel            Ext.Panel　面板
progress         Ext.ProgressBar 进度条
splitbutton      Ext.SplitButton 可分裂的按钮
tabpanel         Ext.TabPanel　选项面板
treepanel        Ext.tree.TreePanel 树
viewport         Ext.ViewPort 视图
window           Ext.Window　窗口

工具栏组件有
---------------------------------------
toolbar          Ext.Toolbar　工具栏
tbbutton         Ext.Toolbar.Button　按钮
tbfill           Ext.Toolbar.Fill　文件
tbitem           Ext.Toolbar.Item　工具条项目
tbseparator      Ext.Toolbar.Separator　工具栏分隔符
tbspacer         Ext.Toolbar.Spacer　工具栏空白
tbsplit          Ext.Toolbar.SplitButton 工具栏分隔按钮
tbtext           Ext.Toolbar.TextItem　工具栏文本项

表单及字段组件包含：
---------------------------------------
form             Ext.FormPanel　Form面板
checkbox         Ext.form.Checkbox　checkbox录入框
combo            Ext.form.ComboBox　combo选择项
datefield        Ext.form.DateField　日期选择项
field            Ext.form.Field　表单字段
fieldset         Ext.form.FieldSet　表单字段组
hidden           Ext.form.Hidden 表单隐藏域
htmleditor       Ext.form.HtmlEditor　html编辑器
numberfield      Ext.form.NumberField　数字编辑器
radio            Ext.form.Radio　单选按钮
textarea         Ext.form.TextArea　区域文本框
textfield        Ext.form.TextField　表单文本框
timefield        Ext.form.TimeField　时间录入项
trigger          Ext.form.TriggerField　触发录入项

可用的vtype列表:
alpha,alphanum,email,url

</span></div>
