SE_API_share
============
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
<h3>5.	中心交易系统通知某笔交易成功</h3>
输入：委托单号，资金账户，金额，是否完成（完成则解冻剩余资金）<br \>
处理：通过委托单号查币种，增减金额<br \>
返回：成功与否<br \>
