# auto_stocken
自动选股，自动交易

## 选股策略(短线)

1. n-grid法则


2. 
```python


# 进场:
# 周k 判断
if macd > macd_before and  dif 和 dea 都在增加:
    加入待选池

# 日k判断
if MACD刚开始大于0 and 未过度上涨:
    if 今天的 dif 比 dea大
        if 0 < dif  and 0 < dea :
            condiction = True
            
if 今天，昨天，前天的macd都大于0:
    if 前天macd > 昨天macd and 今天macd > 昨天macd:
        if 今天dif和dea的差值大于昨天的:
            condition = True
        
if condition = True:
    # 财报判断
    if 上个季度财报营业收入高于这个季度 两个季度中利润都为正值:
        加入日k待选池
        加入进场池
     
对股票排序()

进场()

def 对股票排序():
    
    周k dif和dea的差值  * 0.3 # 无需除上市价，因为如果市价很低，而且涨势很小的话，只能赚个手续费
    近两季度营业额的差值/平均值  * 0.15
    近一个月成交额均值 * 0.2
    近半个月成交额均值 / 近一个月成交额均值 * 0.2
    
    列归一化再求和    


def 进场():
    1. 周k dif和dea曲线无明显趋势不进场 and 周k macd 呈下降趋势不买
    2. dif和dea较大(和macd相比)且几乎相等的不进场

# 出场:
    
    # 方案：使用，前1，前0天平均值进行测试
    
    昨天交易量平均值 = (前天交易量 + 昨天交易量) / 2
    今天交易量平均值 = (昨天交易量 + 今天交易量) / 2
    
    if 涨幅超过 4% or 今天交易量平均值 <= 昨天交易量平均值:
        准备出场()
        
def 准备出场():
    if 明天下跌 < -0.5%(和所盈利的百分比有关):
        出场()
        

# 持仓的数据状态结构

class Deal:
    def __init__(self):
        self.xxx = xxx
        self.stock_log = pd.DataFrame([xxx])

past_deal = [ , dtype=Deal] # 记录已完成的交易
current_deal = [, dtype=Deal] # 记录正在进行的交易
all_stock_log = pd.DataFrame([xxx]) # 记录每支股票的交易


```
1. 使用‘20190830’这天的数据进行尝试，发现符合要求的有87个，按照要求排序后发现前面的效果都非常差
    改进：只取MACD大于0的股票；只提取近3天涨幅并乘上0.5；提取近两周成交量
2. 对不同的股盘分别处理，大股盘，中股盘，小股盘
    
## 选股策略(中线)
    周k入场，日k离场


## 选股策略(长线)


## IDEA
1. MACD和价格有关