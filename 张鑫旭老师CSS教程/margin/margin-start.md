- 正常流向，margin-start 等同于 margin-left，两者重叠不相加
- 如果水平流向是从右向左，margin-start 等同于 margin-right
- 在垂直流下 ( writing-mode:vertical-*; ) margin-start 等同于 margin-top

margin-end 顾名思义

margin-before 默认情况等同于 margin-top

margin-after 等同于 margin-bottom



margin-collapse:collapse;(默认-重叠) 1>1情况

margin-collapse:discard;(取消)  margin重叠 为 0 ，没有margin

margin-collapse:separate;(分隔) margin 重叠为 1+1情况