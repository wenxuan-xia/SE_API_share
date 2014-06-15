SE_API_share
============
<h1>十个默认币种</h1>
CNY人民币
USD美元
EUR欧元
JPY日元
HKD港元
GBP英镑
CAD加拿大元
AUD澳大利亚元
CHF瑞士法郎
SGD新加坡元
<h1>资金账户业务组</h1>
<h2>提供接口：</h2>
<h3>1.	交易客户端查询资金账户：</h3>
输入：证券账户ID<br \>
返回：资金账户ID（数组）<br \>
<h3>2.	查资金账户详情</h3>
输入：资金账户ID<br \>
返回：详情<br \>
<h3>3.	交易客户端验证</h3>
输入：资金账户ID，币种，金额，密码<br \>
处理：验证（不冻结）<br \>
返回：没有对应币种/金额不足/密码错误/正确<br \>

<h3>4.	中心交易系统冻结资金</h3>
输入：委托单号，资金账户ID，币种，金额<br \>
处理：冻结对应资金账户对应币种的对应数量的资金<br \>
返回：成功与否<br \>
<h3>5.	中心交易系统通知买股票成功，扣钱</h3>
输入：委托单号，资金账户I，币种，金额<br \>
处理：买股票，减对应冻结金额<br \>
返回：成功与否<br \>
<h3>6.	中心交易系统通知卖股票成功，加钱</h3>
输入：资金账户ID，币种，金额<br \>
处理：卖股票，加可用余额<br \>
返回：成功与否<br \>
<h3>7.	中心交易系统解冻资金</h3>
输入：委托单号，资金账户ID<br \>
处理：将对资金账户的对应委托单号的冻结资金解冻<br \>
返回：成功与否<br \>

<h2>需求接口：</h2>
<h3>1.	证券账户被冻结</h3>
输入：证券账户ID<br \>
处理：冻结证券账户ID<br \>
返回：成功与否<br \>
<h3>2.	核对身份证号</h3>
输入：证券账户ID, 身份证号<br \>
处理：查询是否匹配<br \>
返回：匹配与否<br \>
<br \>


<h1>中央交易系统</h1>
<br>1.1.1	买卖撤销指令处理组件接口 <br\>
<br>接口函数	AddRecord(stockID,commission_amount,commission_price,commission_time,stockholderID,stockaccountID)<br\>
<br>功能	向中央交易系统输入买卖指令（内部生成委托单号作为主键）<br\>
<br>通信子系统	交易客户端<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	DeleteRecord(commissionID)<br\>
<br>功能	撤销指定委托单（需要与资金、证券账户确认）<br\>
<br>通信子系统	交易客户端<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>1.1.2	查询指令处理组件<br\>
<br>接口函数	GetintervalOpen(start,end,stockId)<br\>
<br>功能	查询指定时间区间内开盘价<br\>
<br>通信子系统	网上信息发布系统<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	GetintervalClose(start,end,stockId)<br\>
<br>功能	查询指定时间区间内收盘价<br\>
<br>通信子系统	网上信息发布系统<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	GetintervalHighest(start,end,stockId)<br\>
<br>功能	查询指定时间区间内最高价<br\>
<br>通信子系统	网上信息发布系统<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	GetintervalLowest(start,end,stockId)<br\>
<br>功能	查询指定时间区间内最低价<br\>
<br>通信子系统	网上信息发布系统<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	Cancel(stockID)<br\>
<br>功能	撤销指定股票的相关交易<br\>
<br>通信子系统	交易管理系统<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	GetCurrentPrice(stockId)<br\>
<br>功能	显示股票最新成交价<br\>
<br>通信子系统	交易管理系统，交易客户端<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	GetCurrentAmount(stockId)<br\>
<br>功能	显示股票最新成交量<br\>
<br>通信子系统	交易管理系统<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	SortBuyPrice(stockId,order=0)<br\>
<br>功能	按照升序显示买入价格<br\>
<br>通信子系统	交易管理系统<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	SortSellPrice(stockId,order=0)<br\>
<br>功能	按照升序显示卖出价格<br\>
<br>通信子系统	交易管理系统<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br><br\>
<br><br\>
<br>接口函数	GetHighestDeal(stockId,type)<br\>
<br>功能	根据输入参数，返回当日最高成交价格，本周最高成交价格，或本月最高成交价格<br\>
<br>通信子系统	交易客户端<br\>
<br>方向	提供给其他模块<br\>
<br><br\>
<br>接口函数	GetLowestDeal(stockId,type)<br\>
<br>功能	根据输入参数，返回当日最低成交价格，本周最低成交价格，或本月最低成交价格<br\>
<br>通信子系统	交易客户端<br\>
<br>方向	提供给其他模块<br\>
<br>1.1.3	交易匹配组件<br\>
<br>接口函数	IfZQTradeSuccess(commissionID,ZQAccountID,amount, stockID,isall)<br\>
<br>功能	向证券账户发出交易请求<br\>
<br>通信子系统	证券账户子系统<br\>
<br>方向	其他模块提供<br\>
<br><br\>
<br>接口函数	IfZJTradeSuccess(commissionID,ZQAccountID,amount, stockID,isall)<br\>
<br>功能	向资金账户发出交易请求<br\>
<br>通信子系统	资金账户子系统<br\>
<br>方向	其他模块提供<br\>
