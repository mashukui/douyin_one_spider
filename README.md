# douyin_one_spider
> 马哥原创：爬抖音聚合软件，采集功能含：搜索评论、主页作品、uid链接转换等。界面GUI软件，对文科生小白友好。
> 
> 本工具仅限学术交流使用，严格遵循相关法律法规，符合平台内容的合法及合规性，禁止用于任何商业用途！

# 一、背景分析与结果展示
## 1.1 开发背景
我是[@马哥python说](https://github.com/mashukui)，一枚10年+程序猿，现全职独立开发。

抖音是国内极具影响力的短视频社交平台，靠着强互动性和庞大的达人创作者群体，已然成为热点事件发酵、优质内容传播的领域。之前，为了满足大家不同的数据采集需求，我分别独立开发了三款软件：针对评论采集的“[爬抖音搜索评论软件](https://github.com/mashukui/douyin_search_comment_tool)”、专门采集特定达人内容的“[爬抖音博主软件](https://github.com/mashukui/douyin_user_post)”，还有专门转换链接uid的“[抖音转换工具](https://github.com/mashukui/dy_trans_tool)”。

这三款软件采集起来挺稳定、数据也全，但部分用户反馈，要是又想采评论又想采主页作品，来回切换软件，用着有点麻烦。为了解决这个问题，我把这三款软件整合到一起了，推出了全新的“**爬抖音聚合软件v1.0**”。这款软件把评论采集、达人主页采集、链接转换这三个核心功能都包含了，提供一站式搞定的抖音数据采集方案。

## 1.2 适用人群与场景
软件适用于：
- 获客截流：从相关行业、品牌热门作品下的评论区精准采集目标用户；
- 数据分析：采集抖音话题数据，用于社会舆情挖掘、网络传播研究等；
- 内容创作：分析优质博主的内容风格、热门话题，为自身创作提供参考；
- 抖音运营：不同格式链接/uid转换，需要跨工具协作的从业者。

## 1.3 结果展示
**【功能1】采集评论**

采集评论界面：
![功能1：采集评论](https://files.mdnice.com/user/32110/fccf81db-b4bb-4c1e-8a51-fcbb591b2dad.jpg)

采集到的作品数据：（共13个字段，含：关键词,页码,视频标题,视频链接,作者昵称,作者uid,作者链接,作者粉丝数,发布时间,点赞数,评论数,收藏数,转发数）
![搜索作品.csv](https://files.mdnice.com/user/32110/aa5fe290-124d-4a22-9a1b-a684016506ed.png)

采集到的评论数据：（共11个字段，含：目标链接,页码,评论者昵称,评论者id,评论者uid,评论者主页链接,评论时间,评论IP属地,评论点赞数,评论级别,评论内容）
![评论.csv](https://files.mdnice.com/user/32110/3f4b82e7-2d00-4aa2-a773-95930fe4db6c.png)

**【功能2】根据主页链接采集作品**

采集主页作品界面：
![功能2：采集主页作品](https://files.mdnice.com/user/32110/4fde9d50-df4e-42ed-b5a7-bf50c4f91872.jpg)

采集主页作品结果：（含17个字段，含：页码,作者昵称,uid,sec_uid,作者链接,作者粉丝数,视频标题,视频标签,视频链接,发布时间,视频时长,是否置顶,点赞数,评论数,收藏数,推荐数,转发数）
![主页作品数据.csv](https://files.mdnice.com/user/32110/0d71bdf1-4e70-4f2c-82ee-1fb093adf649.png)

采集到的主页视频文件：
![自动下载的视频文件](https://files.mdnice.com/user/32110/4b10d3c8-c5fb-4c8c-8b97-c5dff4c27793.png)

**【功能3】链接与uid转换**

转换功能1：主页链接转抖音号
![转换功能1：主页链接转抖音号](https://files.mdnice.com/user/32110/b6b84b34-195f-435f-9352-beddcdb16115.jpg)

转换功能2：抖音号转主页链接（含uid）
![转换功能2：抖音号转主页链接（uid）](https://files.mdnice.com/user/32110/a164b591-db0b-434e-8db9-557547830809.jpg)

转换功能3：app端作品链接转pc端作品链接
![转换功能3：app端作品链接转pc端作品链接](https://files.mdnice.com/user/32110/ba34dce4-724d-4f5b-be0d-3efc418b3be8.jpg)


## 1.4 软件说明

几点说明，请详读：
1. Windows系统、Mac系统均可直接运行，无需配置编程环境
2. 软件含三个核心功能：①根据关键词/作品链接采集评论；②根据主页链接采集作品；③uid转换
3. 软件通过接口协议采集，并非通过模拟浏览器等RPA类，稳定性较高
4. 软件运行完成后，会在当前文件夹（即，软件所在文件夹）生成csv结果文件
5. 采集过程中，每采集一页，存一次csv。并非采完最后一次性保存！防止因异常中断导致丢失前面的数据（每页请求间隔1~2s）
6. 采集过程中，有log文件详细记录运行过程，方便回溯

# 二、主要技术
## 2.1 模块分工
软件全部模块采用python语言开发，主要分工如下： 
```python
tkinter：GUI软件界面
requests：发送请求
json：解析返回的响应数据
pandas：保存csv数据结果
logging：运行过程中日志记录
```
出于版权考虑，暂不公开源码，仅向用户提供软件使用。 

## 2.2 部分代码

部分代码实现： 

发送请求并解析数据：
```python
# 发送请求
r = requests.get(url, headers=h1, params=params)
# 解析数据
json_data = r.json()
```
解析响应数据，以“评论内容”字段为例：
```python
for comment in comment_list:
	# 评论内容
	text = comment['text']
	text_list.append(text)
```
保存结果数据到csv文件：
```python
# 保存数据到DF
df = pd.DataFrame(
	{
		'目标链接': 'https://www.douyin.com/video/' + str(video_id),
		'页码': page,
		'评论者昵称': user_name_list,
		'评论者id': user_unique_id_list,
		'评论者uid': uid_list,
		'评论者主页链接': user_url_list,
		'评论时间': create_time_list,
		'评论IP属地': ip_list,
		'评论点赞数': like_count_list,
		'评论级别': cmt_level_list,
		'评论内容': text_list,
	}
)
# 保存到csv
if os.path.exists(self.result_file2):  # 如果文件存在，不再设置表头
	header = False
else:  # 否则，设置csv文件表头
	header = True
df.to_csv(self.result_file2, mode='a+', index=False, header=header, encoding='utf_8_sig')
self.tk_show('视频[{}]第{}页评论已保存: {}'.format(video_id, page, self.result_file2))
```
底部版权声明：
```python
# 版权信息
copyright = tk.Label(root, text='@马哥python说 All rights reserved.', font=('仿宋', 10), fg='grey')
copyright.place(x=290, y=625)
```
日志记录模块：
```python
def get_logger(self):
    self.logger = logging.getLogger(__name__)
    # 日志格式
    formatter = '[%(asctime)s-%(filename)s][%(funcName)s-%(lineno)d]--%(message)s'
    # 日志级别
    self.logger.setLevel(logging.DEBUG)
    # 控制台日志
    sh = logging.StreamHandler()
    log_formatter = logging.Formatter(formatter, datefmt='%Y-%m-%d %H:%M:%S')
    # info日志文件名
    info_file_name = time.strftime("%Y-%m-%d") + '.log'
    # 将其保存到特定目录
    case_dir = r'./logs/'
    info_handler = TimedRotatingFileHandler(filename=case_dir + info_file_name,
                                        when='MIDNIGHT',
                                        interval=1,
                                        backupCount=7,
                                        encoding='utf-8')
```

# 三、功能与使用
## 3.1 填写cookie
开始采集前，先把自己的cookie值填入cookie.txt文件。

cookie获取说明：
![cookie获取方法](https://files.mdnice.com/user/32110/ac099d27-1673-454f-9ae1-5ee769b6d58b.png)

然后把复制的cookie值填写到当前文件夹的cookie.txt文件中。

## 3.2 软件登录
用户登录界面：需要登录。

## 3.3 启动采集

1）登录成功之后，选择需要的功能模块（搜索帖子/博主帖子/评论）；

2）设置相关参数（如关键词、时间范围、博主链接等）；

3）点击「开始执行」，等待采集完成（可实时查看采集进度）；

4）采集完成后，在默认的当前文件夹中查看csv数据文件或视频下载等。

## 3.4 演示视频
软件使用的完整过程演示视频：[【工具演示】爬抖音聚合软件](https://mp.weixin.qq.com/s/fDb21Rj_kKb_1GNHAJWyIQ)

# 四、付费说明
## 4.1 卡密说明
付费如下：
```python
日卡：使用期限1天，39元。日卡仅能购买一次。适合试用等临时需求
月卡：使用期限1个月，149元。月卡可多次购买。适合短期采集需求
季卡：使用期限3个月，399元。季卡可多次购买。适合中期采集需求
年卡：使用期限1年，799元。年卡可多次购买。适合长期采集需求
```
1）**付费方式一：（手动，付费后加我微信（493882434）对接卡密）**
<img width="2324" height="604" alt="收款码v5" src="https://github.com/user-attachments/assets/69c0d008-6077-420f-b24d-712f58d12fd5" />

2）**付费方式二：（自动， 自己付费自己拿卡密，全程无需加v对接）**

自助开通入口：https://kjyjf.xetlk.com/s/36ksUh

## 4.2 一机一码
为防止软件被恶意转卖，采用一机一码机制，一个卡密只能在一台电脑运行、不可多电脑运行。
## 4.3 软件多开
一台电脑仅允许运行一个软件，不支持软件多开。

## 4.4 软件维护
软件由本人独立原创开发，长期维护更新，提供稳定运行。

# 五、软件获取
公众号"**老男孩的平凡之路**"，后台回复"**爬抖音聚合软件**"获取最新版软件安装包。
<img width="1938" height="364" alt="二维码-公众号放底部v2" src="https://github.com/user-attachments/assets/011b8f02-0b3c-4748-9002-8cc007788bce" />

