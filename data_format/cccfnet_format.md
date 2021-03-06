cccfnet format is designed for cccfnet model

```
5.0|178|1578|237:1.0,470:1.0,587:1.0|7:1.0,8:1.0,16:1.0,19:1.0
2.0|261|324||4:1.0,19:1.0
3.0|560|474||16:1.0,21:1.0
4.0|323|225||7:1.0
4.0|471|4438||7:1.0
4.5|518|1397||4:1.0
5.0|529|431||2:1.0,3:1.0,4:1.0
2.5|14|1446|7:1.0,80:1.0,89:1.0,94:1.0,160:1.0,183:1.0,188:1.0,255:1.0,527:1.0,573:1.0,577:1.0,604:1.0,632:1.0,716:1.0|4:1.0
5.0|594|731||4:1.0,15:1.0,19:1.0
3.0|563|8414||12:1.0
4.5|286|243||2:1.0,3:1.0,4:1.0,19:1.0
4.0|196|1967||7:1.0,9:1.0,20:1.0
5.0|447|197|236:1.0,528:1.0,586:1.0,650:1.0|1:1.0,4:1.0,9:1.0,20:1.0
```
说明：数据分为5列

评分 | userId | itemId | 用户的属性特征 | 物品的属性特征
 
类目 | 说明 | 
----|------| 
评分 | 视具体问题而定，如果是分类问题那就是0/1,否则就是1.0-5.0分 | 
userId | id从0开始计数，userId的总数对应于参数n_user |   
itemId | id从0开始计数，itemId的总数对应于参数n_item | 
用户的属性特征 | 格式为multi-hot类型(feat1:va1, feat2:val2..),如果缺失,则在解析的时候程序自动补上(0:0.0) |   
物品的属性特征 | 格式为multi-hot类型(feat1:va1, feat2:val2..),如果缺失,则在解析的时候程序自动补上(0:0.0) |

cccfnet format是为了cccfnet模型设计的数据格式

tool和该模型相关的code和数据

code | 说明 | 
----|------|
config/cccfnet_regress.yaml,cccfnet_classfy.yaml | 配置文件的例子 |
IO/cccfnet_cache.py | 对cccfnet数据进行解析,压缩成tfrecord |
IO/iterator.py | 读取缓存中之后的tfrecord数据进行训练 |
src/cccfnet.py | 实现模型cccfnet |
train.py | 训练模型的主程序 |
data/cccfnet/train.txt, test.txt, eval.txt | cccfnet实现回归问题的toy 数据 |
data/cccfnet/train_c.txt, test_c.txt, eval_c.txt | cccfnet实现分类问题的toy 数据 |