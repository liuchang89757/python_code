```python
import requests

if __name__ == '__main__':
    # UA伪装：将对应的User-Agent封装到字典中
    headers = {
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36'
    }
    kw = input("请输入要搜索的内容：")
    # 处理url携带的参数：封装到字典中
    url = 'https://www.sogou.com/web'
    params = {
        'query': kw
    }
    # 对指定的url发起的请求对应的url是携带参数的，并且请求过程中处理了参数
    response = requests.get(url=url, params=params, headers=headers)
    page_text = response.text
    filename = kw + '.html'
    with open(filename, 'w', encoding='utf-8') as fp:
        fp.write(page_text)
    print(f'{filename}保存成功！！！')
```



```python
# -*- coding:utf-8 -*-
import requests
import json

if __name__ == '__main__':
    # 指定url
    post_url = 'https://fanyi.baidu.com/sug'
    # post请求参数处理
    word = input('enter a word:')
    data = {
        'kw': word
    }
    # 进行UA伪装
    headers = {
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36'
    }
    # 请求发送post方法,返回响应对象
    response = requests.post(url=post_url, data=data, headers=headers)
    # 获取响应数据，json()方法返回的是obj（如果确认服务器响应数据是json类型的， 才可以使用json()方法）
    # 返回响应的json编码内容
    dict_obj = response.json()
    # print(dict_obj)
    # 持久化存储
    filename = word + '.json'
    with open(filename, 'w', encoding='utf-8') as fp:
        json.dump(obj=dict_obj, fp=fp, ensure_ascii=False)
    # 将 python对象 转化为 json
    # json.dump() 是把python对象转换成json对象生成一个fp的文件流，和文件相关。
    # fp = open('./dog.json', 'w', encoding='utf-8')
    # json.dump(dict_obj, fp=fp, ensure_ascii=False)
    # fp.close()
    print('over!!!')

```



```python
"""
"""
import requests
import json

if __name__ == '__main__':
    # 指定url
    url = 'https://movie.douban.com/j/chart/top_list'
    params = {
        'type': '24',
        'interval_id': '100:90',
        'action': '',
        'start': '0',  # 从库中的第几部取
        'limit': '20'  # 每次取出的数量
    }
    # 进行UA伪装
    headers = {
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36'
    }
    response = requests.get(url=url, params=params, headers=headers)
    list_data = response.json()
    # 持久化存储
    with open('./douban.json', 'w', encoding='utf-8') as fp:
        json.dump(obj=list_data, fp=fp, ensure_ascii=False)

    print('over!!!')

```



```json
[
    {
        "rating":[
            "9.6",
            "50"
        ],
        "rank":1,
        "cover_url":"https://img2.doubanio.com/view/photo/s_ratio_poster/public/p2578474613.jpg",
        "is_playable":true,
        "id":"1292063",
        "types":[
            "剧情",
            "喜剧",
            "爱情",
            "战争"
        ],
        "regions":[
            "意大利"
        ],
        "title":"美丽人生",
        "url":"https://movie.douban.com/subject/1292063/",
        "release_date":"2020-01-03",
        "actor_count":29,
        "vote_count":1212863,
        "score":"9.6",
        "actors":[
            "罗伯托·贝尼尼",
            "尼可莱塔·布拉斯基",
            "乔治·坎塔里尼",
            "朱斯蒂诺·杜拉诺",
            "赛尔乔·比尼·布斯特里克",
            "玛丽萨·帕雷德斯",
            "霍斯特·布赫霍尔茨",
            "利迪娅·阿方西",
            "朱利亚娜·洛约迪切",
            "亚美利哥·丰塔尼",
            "彼得·德·席尔瓦",
            "弗朗西斯·古佐",
            "拉法埃拉·莱博罗尼",
            "克劳迪奥·阿方西",
            "吉尔·巴罗尼",
            "马西莫·比安奇",
            "恩尼奥·孔萨尔维",
            "吉安卡尔洛·科森蒂诺",
            "阿伦·克雷格",
            "汉尼斯·赫尔曼",
            "弗兰科·梅斯科利尼",
            "安东尼奥·普雷斯特",
            "吉娜·诺维勒",
            "理查德·塞梅尔",
            "安德烈提多娜",
            "迪尔克·范登贝格",
            "奥梅罗·安东努蒂",
            "沈晓谦",
            "张欣"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.6",
            "50"
        ],
        "rank":2,
        "cover_url":"https://img9.doubanio.com/view/photo/s_ratio_poster/public/p2354179225.jpg",
        "is_playable":false,
        "id":"5133063",
        "types":[
            "喜剧"
        ],
        "regions":[
            "英国"
        ],
        "title":"憨豆先生精选辑",
        "url":"https://movie.douban.com/subject/5133063/",
        "release_date":"1995-12-15",
        "actor_count":8,
        "vote_count":8918,
        "score":"9.6",
        "actors":[
            "罗温·艾金森",
            "保罗·布朗",
            "理查德·布赖尔斯",
            "安格斯·迪顿",
            "罗宾·德里斯科尔",
            "卡罗琳·昆汀",
            "鲁道夫·沃克尔",
            "理查德·威尔逊"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.5",
            "50"
        ],
        "rank":3,
        "cover_url":"https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2206737207.jpg",
        "is_playable":true,
        "id":"1303408",
        "types":[
            "喜剧",
            "动作",
            "爱情"
        ],
        "regions":[
            "美国"
        ],
        "title":"福尔摩斯二世",
        "url":"https://movie.douban.com/subject/1303408/",
        "release_date":"1924-04-21",
        "actor_count":11,
        "vote_count":22082,
        "score":"9.5",
        "actors":[
            "巴斯特·基顿",
            "凯瑟琳·麦奎尔",
            "乔·基顿",
            "Ward Crane",
            "Jane Connelly",
            "George Davis",
            "Doris Deane",
            "Betsy Ann Hisle",
            "丘比·摩根",
            "John Patrick",
            "Ford West"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.5",
            "50"
        ],
        "rank":4,
        "cover_url":"https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2527089368.jpg",
        "is_playable":false,
        "id":"30203557",
        "types":[
            "喜剧"
        ],
        "regions":[
            "中国香港"
        ],
        "title":"黄子华栋笃笑之金盆𠺘口",
        "url":"https://movie.douban.com/subject/30203557/",
        "release_date":"2018-07-06",
        "actor_count":1,
        "vote_count":3278,
        "score":"9.5",
        "actors":[
            "黄子华"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.4",
            "50"
        ],
        "rank":5,
        "cover_url":"https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2509440210.jpg",
        "is_playable":false,
        "id":"26700818",
        "types":[
            "喜剧",
            "同性"
        ],
        "regions":[
            "英国"
        ],
        "title":"极品基老伴：完结篇",
        "url":"https://movie.douban.com/subject/26700818/",
        "release_date":"2016-06-19",
        "actor_count":10,
        "vote_count":22563,
        "score":"9.4",
        "actors":[
            "伊恩·麦克莱恩",
            "德里克·雅各比",
            "弗朗西斯·德·拉·图瓦",
            "伊万·瑞恩",
            "玛西娅·沃伦",
            "菲利普-沃斯",
            "艾琳·阿特金斯",
            "弗兰西斯·巴贝",
            "阿利斯泰尔·布拉默",
            "理查德·加德"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.4",
            "50"
        ],
        "rank":6,
        "cover_url":"https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2529714509.jpg",
        "is_playable":false,
        "id":"2054458",
        "types":[
            "剧情",
            "喜剧",
            "动画"
        ],
        "regions":[
            "美国"
        ],
        "title":"拽妹黛薇儿要上大学了没",
        "url":"https://movie.douban.com/subject/2054458/",
        "release_date":"2002-01-21",
        "actor_count":10,
        "vote_count":2646,
        "score":"9.4",
        "actors":[
            "吉奥弗瑞·阿伦德",
            "John Lynn",
            "Amir Williams",
            "马克·汤普森",
            "Becca Lish",
            "温迪胡普斯",
            "莎拉·德鲁",
            "Bart Fasbender",
            "费舍·史蒂芬斯",
            "Tracy Grandstaff"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":7,
        "cover_url":"https://img2.doubanio.com/view/photo/s_ratio_poster/public/p1910824951.jpg",
        "is_playable":true,
        "id":"1291549",
        "types":[
            "剧情",
            "喜剧",
            "音乐"
        ],
        "regions":[
            "法国",
            "瑞士",
            "德国"
        ],
        "title":"放牛班的春天",
        "url":"https://movie.douban.com/subject/1291549/",
        "release_date":"2004-10-16",
        "actor_count":17,
        "vote_count":1196972,
        "score":"9.3",
        "actors":[
            "让-巴蒂斯特·莫尼耶",
            "热拉尔·朱尼奥",
            "弗朗索瓦·贝莱昂",
            "凯德·麦拉德",
            "让-保罗·博奈雷",
            "雅克·贝汉",
            "玛丽·布奈尔",
            "马克桑斯·贝汉",
            "格雷戈里·加迪诺尔",
            "托马斯·布伦门塔尔",
            "西里尔·伯尔尼科特",
            "西蒙·法戈特",
            "泰奥杜尔·卡雷-卡赛尼",
            "菲利普·杜·詹纳兰德",
            "埃里克·德斯玛莱茨",
            "狄迪尔·弗拉蒙",
            "卡罗尔·韦斯"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":8,
        "cover_url":"https://img9.doubanio.com/view/photo/s_ratio_poster/public/p1454261925.jpg",
        "is_playable":true,
        "id":"6786002",
        "types":[
            "剧情",
            "喜剧"
        ],
        "regions":[
            "法国"
        ],
        "title":"触不可及",
        "url":"https://movie.douban.com/subject/6786002/",
        "release_date":"2011-11-02",
        "actor_count":17,
        "vote_count":976377,
        "score":"9.3",
        "actors":[
            "弗朗索瓦·克鲁塞",
            "奥玛·希",
            "安娜·勒尼",
            "奥德雷·弗勒罗",
            "约瑟芬娜·德·摩",
            "克洛蒂尔德·莫莱特",
            "阿尔芭·贝露琪",
            "萨丽马特·卡马特",
            "托马·索利韦尔",
            "让-弗朗索瓦·凯雷",
            "玛丽-洛尔·德库洛",
            "安托万·劳伦特",
            "Caroline Bourg",
            "海迪·布奇纳法",
            "艾米丽·卡恩",
            "多萝特博里埃",
            "皮埃尔-罗兰·巴纳隆"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":9,
        "cover_url":"https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2553104888.jpg",
        "is_playable":false,
        "id":"1291858",
        "types":[
            "剧情",
            "喜剧"
        ],
        "regions":[
            "中国大陆"
        ],
        "title":"鬼子来了",
        "url":"https://movie.douban.com/subject/1291858/",
        "release_date":"2000-05-12",
        "actor_count":30,
        "vote_count":565275,
        "score":"9.3",
        "actors":[
            "姜文",
            "香川照之",
            "袁丁",
            "姜宏波",
            "丛志军",
            "李丛喜",
            "泽田谦也",
            "李海滨",
            "蔡卫东",
            "陈述",
            "陈莲梅",
            "史建全",
            "陈强",
            "宫路佳具",
            "吴大维",
            "梶冈润一",
            "石山雄大",
            "述平",
            "姜武",
            "姜金才",
            "石山雄太",
            "山田将之",
            "贾幼然",
            "王义和",
            "杜世儒",
            "周海超",
            "白云生",
            "徐海东",
            "长野客弘",
            "鱼见亮介"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":10,
        "cover_url":"https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2263408369.jpg",
        "is_playable":true,
        "id":"1294371",
        "types":[
            "剧情",
            "喜剧",
            "爱情"
        ],
        "regions":[
            "美国"
        ],
        "title":"摩登时代",
        "url":"https://movie.douban.com/subject/1294371/",
        "release_date":"1936-02-25",
        "actor_count":37,
        "vote_count":270140,
        "score":"9.3",
        "actors":[
            "查理·卓别林",
            "宝莲·高黛",
            "亨利·伯格曼",
            "蒂尼·桑福德",
            "切斯特·康克林",
            "汉克·曼",
            "斯坦利·布莱斯通",
            "阿尔·欧内斯特·加西亚",
            "理查德·亚历山大",
            "塞西尔·雷诺兹",
            "米拉·麦金尼",
            "默多克·麦夸里",
            "威尔弗雷德·卢卡斯",
            "爱德华·勒桑",
            "弗雷德·马拉泰斯塔",
            "萨米·斯坦",
            "特德·奥利弗",
            "诺曼·安斯利",
            "博比·巴伯",
            "海尼·康克林",
            "格洛丽亚·德黑文",
            "帕特·弗莱厄蒂",
            "弗兰克·哈格尼",
            "帕特·哈蒙",
            "劳埃德·英格拉哈姆",
            "沃尔特·詹姆斯",
            "爱德华·金博尔",
            "杰克·洛",
            "巴迪·梅辛杰",
            "布鲁斯·米切尔",
            "弗兰克·莫兰",
            "詹姆斯·C·莫顿",
            "路易·纳托",
            "J·C·纽金特",
            "拉斯·鲍威尔",
            "约翰兰德",
            "哈里·威尔逊"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":11,
        "cover_url":"https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2170238828.jpg",
        "is_playable":true,
        "id":"1293908",
        "types":[
            "喜剧",
            "剧情",
            "爱情"
        ],
        "regions":[
            "美国"
        ],
        "title":"城市之光",
        "url":"https://movie.douban.com/subject/1293908/",
        "release_date":"1931-01-30",
        "actor_count":9,
        "vote_count":128977,
        "score":"9.3",
        "actors":[
            "查理·卓别林",
            "弗吉尼亚·切瑞尔",
            "佛罗伦斯·李",
            "亨利·伯格曼",
            "珍·哈露",
            "哈利·迈耶斯",
            "约翰兰德",
            "罗伯特·帕里什",
            "罗伯特·格雷夫斯"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":12,
        "cover_url":"https://img3.doubanio.com/view/photo/s_ratio_poster/public/p2409467410.jpg",
        "is_playable":false,
        "id":"26946612",
        "types":[
            "剧情",
            "喜剧",
            "爱情",
            "动画"
        ],
        "regions":[
            "中国大陆"
        ],
        "title":"狐妖小红娘剧场版：王权富贵",
        "url":"https://movie.douban.com/subject/26946612/",
        "release_date":"2016-05-20",
        "actor_count":7,
        "vote_count":11984,
        "score":"9.3",
        "actors":[
            "杨天翔",
            "刘校妤",
            "乔诗语",
            "魏超",
            "阎萌萌",
            "张凯",
            "范哲琛"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":13,
        "cover_url":"https://img2.doubanio.com/view/photo/s_ratio_poster/public/p2533925433.jpg",
        "is_playable":false,
        "id":"30312425",
        "types":[
            "喜剧"
        ],
        "regions":[
            "美国"
        ],
        "title":"丹尼尔·斯洛斯：现场表演",
        "url":"https://movie.douban.com/subject/30312425/",
        "release_date":"2018-09-11",
        "actor_count":1,
        "vote_count":4948,
        "score":"9.3",
        "actors":[
            "丹尼尔·斯洛斯"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":14,
        "cover_url":"https://img9.doubanio.com/view/photo/s_ratio_poster/public/p2184490255.jpg",
        "is_playable":false,
        "id":"6309377",
        "types":[
            "喜剧"
        ],
        "regions":[
            "英国"
        ],
        "title":"西蒙·阿姆斯特尔：顺其自然",
        "url":"https://movie.douban.com/subject/6309377/",
        "release_date":"2010",
        "actor_count":1,
        "vote_count":3459,
        "score":"9.3",
        "actors":[
            "西蒙·阿姆斯特尔"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.3",
            "50"
        ],
        "rank":15,
        "cover_url":"https://img9.doubanio.com/view/photo/s_ratio_poster/public/p2212596294.jpg",
        "is_playable":true,
        "id":"26264388",
        "types":[
            "剧情",
            "喜剧",
            "音乐"
        ],
        "regions":[
            "英国"
        ],
        "title":"跳出我天地音乐剧",
        "url":"https://movie.douban.com/subject/26264388/",
        "release_date":"2014-09-28",
        "actor_count":6,
        "vote_count":1480,
        "score":"9.3",
        "actors":[
            "鲁茜·亨肖",
            "利亚姆·莫威尔",
            "霍华德·克罗斯利",
            "汤姆·赫兰德",
            "艾力厄特·翰纳",
            "伊莫珍·古尼"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.2",
            "50"
        ],
        "rank":16,
        "cover_url":"https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2614500649.jpg",
        "is_playable":true,
        "id":"25662329",
        "types":[
            "喜剧",
            "动画",
            "冒险"
        ],
        "regions":[
            "美国"
        ],
        "title":"疯狂动物城",
        "url":"https://movie.douban.com/subject/25662329/",
        "release_date":"2016-03-04",
        "actor_count":42,
        "vote_count":1729235,
        "score":"9.2",
        "actors":[
            "金妮弗·古德温",
            "杰森·贝特曼",
            "伊德里斯·艾尔巴",
            "珍妮·斯蕾特",
            "内特·托伦斯",
            "邦尼·亨特",
            "唐·雷克",
            "汤米·钟",
            "J·K·西蒙斯",
            "奥克塔维亚·斯宾瑟",
            "艾伦·图代克",
            "夏奇拉",
            "雷蒙德·S·佩尔西",
            "德拉·萨巴",
            "莫里斯·拉马奇",
            "菲尔·约翰斯顿",
            "约翰·迪·马吉欧",
            "凯蒂·洛斯",
            "吉塔·雷迪",
            "杰西·科尔蒂",
            "汤米·利斯特",
            "乔希·达拉斯",
            "瑞奇·摩尔",
            "凯斯·索西",
            "彼得·曼斯布里奇",
            "拜伦·霍华德",
            "杰拉德·布什",
            "马克·史密斯",
            "乔西·特立尼达",
            "约翰·拉维尔",
            "克里斯汀·贝尔",
            "吉尔·科德斯",
            "梅利莎·古德温",
            "尼古拉斯·格斯特",
            "佟心竹",
            "张震",
            "李楠",
            "季冠霖",
            "容祖儿",
            "黄子华",
            "蔡依林",
            "戴维德·迪格斯"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.2",
            "50"
        ],
        "rank":17,
        "cover_url":"https://img2.doubanio.com/view/photo/s_ratio_poster/public/p579729551.jpg",
        "is_playable":true,
        "id":"3793023",
        "types":[
            "剧情",
            "喜剧",
            "爱情",
            "歌舞"
        ],
        "regions":[
            "印度"
        ],
        "title":"三傻大闹宝莱坞",
        "url":"https://movie.douban.com/subject/3793023/",
        "release_date":"2011-12-08",
        "actor_count":13,
        "vote_count":1715573,
        "score":"9.2",
        "actors":[
            "阿米尔·汗",
            "卡琳娜·卡普尔",
            "马达范",
            "沙尔曼·乔希",
            "奥米·瓦依达",
            "博曼·伊拉尼",
            "莫娜·辛格",
            "拉杰夫·拉宾德拉纳特安",
            "Atul Tiwari",
            "阿里·法扎勒",
            "帕里卡沙特.萨赫尼",
            "Rakesh Sharma",
            "贾维德·杰弗里"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.2",
            "45"
        ],
        "rank":18,
        "cover_url":"https://img9.doubanio.com/view/photo/s_ratio_poster/public/p2455050536.jpg",
        "is_playable":true,
        "id":"1292213",
        "types":[
            "喜剧",
            "爱情",
            "奇幻",
            "古装"
        ],
        "regions":[
            "中国香港",
            "中国大陆"
        ],
        "title":"大话西游之大圣娶亲",
        "url":"https://movie.douban.com/subject/1292213/",
        "release_date":"2014-10-24",
        "actor_count":17,
        "vote_count":1404506,
        "score":"9.2",
        "actors":[
            "周星驰",
            "吴孟达",
            "朱茵",
            "蔡少芬",
            "蓝洁瑛",
            "莫文蔚",
            "罗家英",
            "刘镇伟",
            "陆树铭",
            "李健仁",
            "胡立成",
            "金永钢",
            "付博文",
            "许敬义",
            "江约诚",
            "吴珏瑾",
            "侯艳"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.2",
            "45"
        ],
        "rank":19,
        "cover_url":"https://img9.doubanio.com/view/photo/s_ratio_poster/public/p1960167314.jpg",
        "is_playable":true,
        "id":"1295646",
        "types":[
            "喜剧",
            "剧情",
            "战争"
        ],
        "regions":[
            "美国"
        ],
        "title":"大独裁者",
        "url":"https://movie.douban.com/subject/1295646/",
        "release_date":"1940-10-15",
        "actor_count":8,
        "vote_count":69142,
        "score":"9.2",
        "actors":[
            "查理·卓别林",
            "宝莲·高黛",
            "杰克·奥克",
            "雷金纳德·加德纳",
            "卡特·德黑文",
            "比利·吉尔伯特",
            "格蕾斯·海尔",
            "邱岳峰"
        ],
        "is_watched":false
    },
    {
        "rating":[
            "9.2",
            "50"
        ],
        "rank":20,
        "cover_url":"https://img2.doubanio.com/view/photo/s_ratio_poster/public/p2649579601.jpg",
        "is_playable":true,
        "id":"34908189",
        "types":[
            "喜剧",
            "爱情"
        ],
        "regions":[
            "美国"
        ],
        "title":"老友记重聚特辑",
        "url":"https://movie.douban.com/subject/34908189/",
        "release_date":"2021-05-27",
        "actor_count":33,
        "vote_count":67107,
        "score":"9.2",
        "actors":[
            "詹妮弗·安妮斯顿",
            "柯特妮·考克斯",
            "马修·派瑞",
            "大卫·休默",
            "丽莎·库卓",
            "马特·勒布朗",
            "瑞茜·威瑟斯彭",
            "Lady Gaga",
            "大卫·贝克汉姆",
            "贾斯汀·比伯",
            "詹姆斯·柯登",
            "辛迪·克劳馥",
            "卡拉·迪瓦伊",
            "埃利奥特·古尔德",
            "基特·哈灵顿",
            "拉里·哈金",
            "敏迪·卡灵",
            "托马斯·列农",
            "克里斯蒂娜·皮克勒斯",
            "汤姆·塞立克",
            "詹姆斯·迈克尔·泰勒",
            "玛姬·惠勒",
            "马拉拉·尤萨夫扎伊",
            "金南俊",
            "凯文·布莱特",
            "玛尔塔·考夫曼",
            "大卫·克拉尼",
            "金硕珍",
            "郑号锡",
            "朴智旻",
            "金泰亨",
            "田柾国",
            "闵玧其"
        ],
        "is_watched":false
    }
]
```



```python
"""

"""
import requests
import json

if __name__ == '__main__':
    # 指定url
    url = 'http://www.kfc.com.cn/kfccda/ashx/GetStoreList.ashx?op=keyword'
    data = {
        'cname': '',
        'pid': '',
        'keyword': '西安',
        'pageIndex': '1',
        'pageSize': '10'
    }
    headers = {
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36'
    }
    # 发起post请求
    response = requests.post(url=url, data=data, headers=headers)
    page_text = response.json()
    with open('kfc_page.json', 'w', encoding='utf-8') as fp:
        json.dump(obj=page_text, fp=fp, ensure_ascii=False)

    print('over!!!')

```



```

```

```python
import requests
import re
import os

if __name__ == '__main__':
    # 创建一个文件夹
    if not os.path.exists('./costulibs'):
        os.mkdir('./costulibs')
    # 指定url
    url = 'http://www.cosplay8.com/pic/chinacos/'
    # UA伪装
    headers = {
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36'
    }
    # 发送请求
    page_text = requests.get(url=url, headers=headers).content.decode('utf-8')
    ex = '<a href=.*?<img src=\'(.*?)\' border=.*?</a>'
    img_src_list = re.findall(ex, page_text, re.S)
    for src in img_src_list:
        # 拼接出完成的图片url
        src = 'http://www.cosplay8.com' + src
        # 请求到图片的二进制数据
        img_data = requests.get(url=src, headers=headers).content
        # 生成图片名称
        img_name = src.split('/')[-1]
        # 图片存储路径
        imgPath = './costulibs/' + img_name
        # 持久化存储图片
        with open(imgPath, 'wb') as fp:
            fp.write(img_data)
            print(img_name, '下载成功！')
```



```python
import requests
import re
import os

if __name__ == '__main__':
    # 创建一个文件夹
    if not os.path.exists('./costulibs'):
        os.mkdir('./costulibs')
    for i in range(1, 108):
        # 指定url
        url = 'http://www.cosplay8.com/pic/chinacos/list_22_' + str(i) + '.html'
        # UA伪装
        headers = {
            'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36'
        }
        # 发送请求
        page_text = requests.get(url=url, headers=headers).content.decode('utf-8')
        ex = '<a href=.*?<img src=\'(.*?)\' border=.*?</a>'
        img_src_list = re.findall(ex, page_text, re.S)
        for src in img_src_list:
            # 拼接出完成的图片url
            src = 'http://www.cosplay8.com' + src
            # 请求到图片的二进制数据
            img_data = requests.get(url=src, headers=headers).content
            # 生成图片名称
            img_name = src.split('/')[-1]
            # 图片存储路径
            imgPath = './costulibs/' + img_name
            # 持久化存储图片
            with open(imgPath, 'wb') as fp:
                fp.write(img_data)
                print(img_name, '下载成功！')


```



```python
# 58同城二手房信息title抓取
import requests
from lxml import etree

if __name__ == '__main__':
    # 爬取到页面源码数据
    url = 'https://xa.58.com/ershoufang/p1/'
    headers = {
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36'
    }
    # get请求
    page_text = requests.get(url=url, headers=headers).text
    # 数据解析
    tree = etree.HTML(page_text)
    # 房屋名称信息
    house_title_list = tree.xpath('//div[@class="property-content-title"]/h3/text()')
    with open('./58title.txt', 'w', encoding='utf-8') as fp:
        for list_name in house_title_list:
            fp.write(list_name + '\n')
            print("房屋title写入完成 ===》 " + list_name)

```



```python
"""
爬取梨视频的视频数据
原则：线程池处理的是阻塞且耗时的操作
multiprocessing.Pool常用函数解析
apply_async(func[, args[, kwds]]) ：使用非阻塞方式调用func（并行执行，堵塞方式必须等待上一个进程退出才能执行下一个进程），args为传递给func的参数列表，kwds为传递给func的关键字参数列表；
close()：关闭Pool，使其不再接受新的任务；
terminate()：不管任务是否完成，立即终止；
join()：主进程阻塞，等待子进程的退出， 必须在close或terminate之后使用；

"""
import requests
from lxml import etree
import os
from multiprocessing.dummy import Pool

# UA伪装
headers = {
    'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36'
}
# 对下述url发起请求，解析视频详情页的url和视频的名称
url = 'https://www.pearvideo.com/category_5'
page_text = requests.get(url=url, headers=headers).text
# 实例化etree对象
tree = etree.HTML(page_text)
# 解析视频的视频id和视频名称
video_id_list = tree.xpath(
    "//ul[@class='listvideo-list clearfix']/li[@class='categoryem ']//a[@class='vervideo-lilink actplay']/@href")
video_name_list = tree.xpath(
    "//ul[@class='listvideo-list clearfix']/li[@class='categoryem ']//a/div[@class='vervideo-title']/text()")
# print(video_name_list, video_id_list)
# 列表生成式存储视频id和视频名称
data_list = [{"name": video_name_list[i], "idNum": video_id_list[i][6:]} for i in range(len(video_name_list))]
# 创建一个存放视频的文件夹
if not os.path.exists("./videos"):
    os.mkdir("./videos")


# 获取视频的函数
def down_video(data):
    name = data['name']
    idNum = data['idNum']
    # UA伪装
    # 获取视频需要的headers，注意这里的Referer要和视频的id匹配，为什么这里需要Referer呢？？？
    # http referer是header的一部分，当浏览器向web服务器发送请求的时候，一般会带上referer，告诉服务器该网页是从那个页面链接
    # 过来的，服务器因此可以获得一些信息用于处理
    headers = {
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36',
        'Referer': f'https://www.pearvideo.com/video_{idNum}'
    }
    url = f'https://www.pearvideo.com/videoStatus.jsp?contId={idNum}'
    # 得到包含视频地址json响应数据
    response = requests.get(url=url, headers=headers).json()
    video_url = response["videoInfo"]["videos"]["srcUrl"]
    # 将视频地址中的数字替换成 cont-视频编号 拿到真正的视频地址
    video_url = video_url.replace(video_url.split("/")[-1].split("-")[0], "cont-" + idNum)
    # 拿到视频并持久化存储
    video = requests.get(url=video_url, headers=headers).content
    with open(f"./videos/{name}.mp4", "wb") as fp:
        print(f"正在下载视频---{name}...")
        fp.write(video)
        print(f"视频{name}---下载完成!")


if __name__ == '__main__':
    # 创建进程池并使用
    pool = Pool(3)
    # 对 'iterable' 中的每个元素应用 'func'，在返回的列表中收集结果
    pool.map(down_video, data_list)
    # 关闭Pool，使其不再接受新的任务
    pool.close()
    # 主进程阻塞，等待子进程的退出， 必须在close或terminate之后使用
    pool.join()

```



```
单线程+异步协程(推荐) :
event_ loop:事件循环，相当于一个无限循环，我们可以把一些函数注册到这 个事件循环上，
当满足某些条件的时候，函数就会被循环执行。
coroutine:协程对象，我们可以将协程对象注册到事件循环中，它会被事件循环调用。
我们可以使用async 关键字来定义一个方法，这个方法在调用时不会立即被执行，而是返回
一个协程对象。
task:任务，它是对协程对象的进一步封装， 包含了任务的各个状态。
future:代表将来执行或还没有执行的任务，实际上和task没有本质区别。
async定义一个协程.
await用来挂起阻塞方法的执行。
```



```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
import time

# Object that manages the starting and stopping of the ChromeDriver
s = Service(executable_path='./chromedriver')
bro = webdriver.Chrome(service=s)
bro.get('https://www.taobao.com/')
# 标签定位
# search_input = bro.find_element_by_id("q")
search_input = bro.find_element(by=By.ID, value="q")
# 标签交互
search_input.send_keys('iphone')
time.sleep(1)
# 执行一组js程序
bro.execute_script('window.scrollTo(0,document.body.scrollHeight)')
time.sleep(2)
# 标签定位
# btn = bro.find_element_by_css_selector('.btn-search')
btn = bro.find_element(by=By.CSS_SELECTOR, value='.btn-search')
# 点击搜索按钮
btn.click()
# 请求网站
bro.get('https://www.baidu.com')
time.sleep(2)
# 浏览器回退
bro.back()
time.sleep(2)
# 浏览器前进
bro.forward()
time.sleep(2)
# 休眠sleep
time.sleep(2)
# 关闭浏览器
bro.quit()
```



```python
# 无浏览器界面+反检测
from selenium import webdriver
from time import sleep
from selenium.webdriver.chrome.service import Service
from selenium.webdriver import ChromeOptions

option = ChromeOptions()
# 实现规避检测
option.add_experimental_option('excludeSwitches', ['enable-automation'])
# 实现无可视化浏览器界面
option.add_argument('--headless')
option.add_argument('--disable-gpu')

s = Service(executable_path='./chromedriver')
bro = webdriver.Chrome(service=s, options=option)
bro.get('https://www.baidu.com')
print(bro.page_source)
sleep(2)
bro.quit()

```

