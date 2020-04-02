02. Pandas读取数据
本代码演示：

pandas读取纯文本文件
读取csv文件
读取txt文件
pandas读取xlsx格式excel文件
pandas读取mysql数据表
import pandas as pd
1、读取纯文本文件
1.1 读取CSV，使用默认的标题行、逗号分隔符
fpath = "./datas/ml-latest-small/ratings.csv"
# 使用pd.read_csv读取数据
ratings = pd.read_csv(fpath)
# 查看前几行数据
ratings.head()
userId	movieId	rating	timestamp
0	1	1	4.0	964982703
1	1	3	4.0	964981247
2	1	6	4.0	964982224
3	1	47	5.0	964983815
4	1	50	5.0	964982931
# 查看数据的形状，返回(行数、列数)
ratings.shape
(100836, 4)
# 查看列名列表
ratings.columns
Index(['userId', 'movieId', 'rating', 'timestamp'], dtype='object')
# 查看索引列
ratings.index
RangeIndex(start=0, stop=100836, step=1)
# 查看每列的数据类型
ratings.dtypes
userId         int64
movieId        int64
rating       float64
timestamp      int64
dtype: object
1.2 读取txt文件，自己指定分隔符、列名
fpath = "./datas/crazyant/access_pvuv.txt"
pvuv = pd.read_csv(
    fpath,
    sep="\t",
    header=None,
    names=['pdate', 'pv', 'uv']
)
pvuv
pdate	pv	uv
0	2019-09-10	139	92
1	2019-09-09	185	153
2	2019-09-08	123	59
3	2019-09-07	65	40
4	2019-09-06	157	98
5	2019-09-05	205	151
6	2019-09-04	196	167
7	2019-09-03	216	176
8	2019-09-02	227	148
9	2019-09-01	105	61
2、读取excel文件
fpath = "./datas/crazyant/access_pvuv.xlsx"
pvuv = pd.read_excel(fpath)
pvuv
日期	PV	UV
0	2019-09-10	139	92
1	2019-09-09	185	153
2	2019-09-08	123	59
3	2019-09-07	65	40
4	2019-09-06	157	98
5	2019-09-05	205	151
6	2019-09-04	196	167
7	2019-09-03	216	176
8	2019-09-02	227	148
9	2019-09-01	105	61
3、读取MySQL数据库
import pymysql
conn = pymysql.connect(
        host='127.0.0.1',
        user='root',
        password='12345678',
        database='test',
        charset='utf8'
    )
mysql_page = pd.read_sql("select * from crazyant_pvuv", con=conn)
mysql_page
pdate	pv	uv
0	2019-09-10	139	92
1	2019-09-09	185	153
2	2019-09-08	123	59
3	2019-09-07	65	40
4	2019-09-06	157	98
5	2019-09-05	205	151
6	2019-09-04	196	167
7	2019-09-03	216	176
8	2019-09-02	227	148
9	2019-09-01	105	61
​
