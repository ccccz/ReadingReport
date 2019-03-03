
> 此内容为不完全摘取，摘录了私以为可能会用到的信息，所有翻译来自有道/个人（六级没过的英语水平），如有错误，emmmm，帮忙改一下吧。      ——CZ

## Chapter 4
 - 如果两条路有交叉或者连接，那么他们一定是有共同的node的【Ways can cross without being joined, and you should only assume ways are physically connected if they share a node, or more than one node. Conversely, you should only join two ways with a node if they actually physically connect. 】
 - 路的ref是node的id
 - relations是三种基本类型的列表（包括其他relations）。relations的存在是为了描述不能用node或way进行描述的特征，或者是同一个type有两个feature
 - changeset不是数据模型的一部分，而是对数据所做的更改，是变更活动的记录，关闭后不可更改。引入changeset是为了更容易识别地图的相关变更，并整理数据的属性。
 - changeset不包含更改本身的细节，且与基本数据存储在不同文件中
 - OSM服务器使用UTF-8编码
 - tag是语义的（？），不能改变地图外观（应该是这个意思，翻译失败，以下是原文）【Tagging is semantic, in that you describe the properties of a feature you're mapping, rather than describing how you'd like it to appear on the map. The appearance of any feature on a map based on OpenStreetMap data is entirely under the control of the person who configures the renderer for that map. There's no way to force a particular feature to look a particular way in any renderer.】
 - 键值对的含义在维基百科[【Map_Features】](http://wiki.openstreetmap.org/wiki/) [【搜索其他标记】](http://bit.ly/osmsearch)
 - key=highway value=*这个键值对表示道路，任何公共道路都OK（英式用法），而不是仅指高速公路![主要值](/api/file/getImage?fileId=5c7502c91a9c9104c90005b2)
 - 更多的![图片标题](/api/file/getImage?fileId=5c7506b01a9c9104c90005b4)![图片标题](/api/file/getImage?fileId=5c7506e11a9c9104c90005b5)


## Chapter 9

 - 一个专用工具wget
 - 在```http://planet.openstreetmap.org/```网站上下载所需数据,书上给出的信息是2010年压缩包只有8.1GB，但现在压缩包也有74GB了orz。
 - 可以用wget直接检索压缩包√
 - 提取网站，可以直接下载某一大洲或某一国家的地图资料```http://download.geofabrik.de/osm/```   ``` http://downloads.cloudmade.com/```
 - 之前提到的，直接从osm数据库加载数据过慢这个问题，怎么说，osm不支持重复使用主API（不清楚那个方法是不是调用的主API）检索大量数据，书上说会封号（无法使用osm服务器），所以还是使用离线地图叭，中国地图压缩包只有845MB，就是下载速度有点慢
 - 查找单个节点```wget -O compton-node.osm http://api.openstreetmap.org/api/0.6（版本号）/node（数据类型）/30361710（id）[/ways]（可选，仅限node，可获得包含此节点的所有way，也可以换为relations）```
 - 可以使用```http://api.openstreetmap.org/api/0.6/map?bbox=<left>,<bottom>,<right>,<top>```方法来获取一个范围（方块）内的osm文件（各类信息），范围限制在0.25经纬度以及50000个节点内，更大范围的话可以使用XAPI![图片标题](/api/file/getImage?fileId=5c789c7d1a9c9104c90005ff)
 ```
wget -O iceland-ways.osm http://xapi.openstreetmap.org/api/0.6/way[bbox=- 25.09,62.94,-12.55,67.42]     //获取特定类型节点
 wget -O iceland-coastline.osm http://xapi.openstreetmap.org/api/0.6/way[bbox=-25.09,62.94,-12.55,67.42][natural=coastline]     //获取特定特性的节点
```
- XAPI[维基百科](http://wiki.openstreetmap.org/wiki/XAPI)
- 功能极多详见chapter 9


## Chapter 10
- 主要内容为使用osmosis来操控数据
- 也可以用来提取数据，类似osm API
