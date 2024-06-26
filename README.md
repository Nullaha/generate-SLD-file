
## 使用

修改 example/input 中的内容，然后运行 run.py  

example/input/data.py中保存的是数据。

如果是图片的点样式，需要将图片放到example/input/img/对应路径下。


## 介绍

生成几种简单的sld样式

|TODO | 类型 | 名称 | 说明 |
|-----| ---- | ---- | ---- |
|  | 线 | line-simple | 简单的线 |
|  | 线 | line-filter | 字段等于A是A样式，字段等于B是B样式 |
|  | 线 | line-dasharray | 虚线 |
|  | 线 | line-multi | 两条线叠一起用 |
|  | 面 | polygon-nostroke | 只有填充色，没有边界线 |
|  | 面 | polygon-fill-slash | 几种填充 |
|  | 面 | polygon-stroke |有填充色，也有边界线 |
|  | 面 | polygon-filter | 字段等于A是A样式，字段等于B是B样式 |
|  | 点 | point-base64 | 是图片的点样式 |
| TODO | 点 | point-? |其它简单的点样式这里暂时没有 |



## line-simple 

```py
    # line-simple: 不需要判断字段：1个rule，一条实线
    {
    "dir":"example/line-simple",
    "layer_name": "高速铁路",
    "rules": [
        {
            "name": "高速铁路",
            "type": "line",
            # "filter": {
            #   "name": "判断的字段",
            #   "value": "判断的值",
            # },
            "symbolizer": [
                {
                "stroke": {
                    'text': rgb_to_hex(255,	0, 0),
                    'width': "1.5",
                    # "dasharray":"4 6"
                    },

            },
                
            ]
        }
    ]
    }
```

![line-simple](./docs/snapshot/line-simple.png)

## line-filter 

```py
 { # 需要判断字段：多个rule
   "dir":"example/line-filter",
    "layer_name": "高速铁路",
    "rules": [
        {
            "name": "一级",
            "type": "line",
            "filter": {
              "name": "类型",
              "value": "一级",
            },
            "symbolizer": [
               {
                "stroke": {
                    'text': rgb_to_hex(255,	0, 0),
                    'width': "1.1",
                    # "dasharray":"4 6"
                  },

            },
              
            ]
        },
        {
            "name": "二级",
            "type": "line",
            "filter": {
              "name": "类型",
              "value": "二级",
            },
            "symbolizer": [
               {
                "stroke": {
                    'text': rgb_to_hex(0, 0, 255),
                    'width': "1.0",
                    # "dasharray":"4 6"
                  },

            },
              
            ]
        },
    ]
},
```

## line-dasharray 

```py
{
   "dir":"example/line-dasharray",
    "layer_name": "高速铁路",
    "rules": [
        {
            "name": "高速铁路",
            "type": "line",
            "symbolizer": [
               {
                "stroke": {
                    'text': rgb_to_hex(255,	0, 0),
                    'width': "1.0",
                    "dasharray":"20 6 20 6 1 6 1 6"
                  },

            },
              
            ]
        }
    ]
},
```
![line-simple](./docs/snapshot/line-dasharray.png)

## line-multi 

```py
{# 两条不同颜色的线：多个symbolizer，先写粗的再写细的，虚线加dasharray
   "dir":"example/line-multi",
    "layer_name": "高速铁路",
    "rules": [
        {
            "name": "高速铁路",
            "type": "line",
            "symbolizer": [
               {
                "stroke": {
                    'text': rgb_to_hex(100,	100,	100),
                    'width': "1.5",
                    # "dasharray":"4 6"
                  },

            },
               {
                "stroke": {
                    'text': rgb_to_hex(245,	245,	245),
                    'width': "1.0",
                    "dasharray":"4 6"
                  },

            },
              
            ]
        }
    ]
},
```
![line-simple](./docs/snapshot/line-multi.png)

## polygon-nostroke 

```py
 {
    "dir": "example/polygon-nostroke",
    "layer_name": "水库工程",
    "rules": [
        {
            "name": "大型",
            "type": "polygon",
            "symbolizer": {
                "fill": {
                    "text": rgb_to_hex(0, 87, 255)
                }
            },
        },
     
    ]
},
```

![polygon-nostroke](./docs/snapshot/polygon-nostroke.png)

## polygon-stroke 

```py
 {
    "dir": "example/polygon-stroke",
    "layer_name": "水库工程",
    "rules": [
        {
            "name": "大型",
            "type": "polygon",
            "symbolizer": {
                "fill": {
                    "text": rgb_to_hex(0, 87, 255)
                },
                "stroke": {
                    'text': rgb_to_hex(211, 255, 0),
                    'width': "0.1"
                }
            },
        },
     
    ]
},
```

![polygon-stroke](./docs/snapshot/polygon-stroke.png)

## polygon-filter 

```py
  {
    "dir": "example/polygon-filter",
    "layer_name": "水库工程",
    "rules": [
        {
            "name": "大型",
            "type": "polygon",
            "filter": {
                "name": "等级",
                "value": "大型",
            },
            "symbolizer": {
                "fill": {
                    "text": rgb_to_hex(0, 87, 255)
                },
                "stroke": {
                    'text': rgb_to_hex(211, 255, 0),
                    'width': "0.1"
                }
            },
        },
        {
            "name": "中型",
            "type": "polygon",
            "filter": {
                "name": "等级",
                "value": "中型",
            },
            "symbolizer": {
                "fill": {
                    "text": rgb_to_hex(219, 247, 193)
                }
            },
        },
    ]
},
```

## polygon-fill-slash 

```py
  {
    "dir": "example/polygon-fill-slash",
    "layer_name": "水库工程",
    "rules": [
        {
            "name": "大型",
            "type": "polygon_slash",
            "symbolizer": {
                "fill": {
                    "text": rgb_to_hex(255, 170, 0)
                },
                "slash":{
                  "shape":"times", 
                },
                "stroke": {
                    'text': rgb_to_hex(255, 170, 0),
                    'width': "0.35"
                }
            },
        },
    ]
},

```

![polygon-fill-slash](./docs/snapshot/polygon-fill-slash.png)

## point-base64

```py
  {
  "dir":"example/point-base64",
   "layer_name": "矿山",
   "rules": [
       {
           "name": "地下水",
           "type": "point",
          #  "filter": {
          #    "name": "矿种名称",
          #    "value": "地下水",
          #  },
           "symbolizer": {
               "size":"10",
               "base64":""

           },
       }, 
        
   ],
   
}
```

![point-base64](./docs/snapshot/point-base64.png)

