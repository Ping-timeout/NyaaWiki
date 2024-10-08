# NyaaBank 操作向导

!> :construction: **NyaaBank 已终止服务，内容仅供参考。**

本页记录适用于普通玩家和银行家的NyaaBank（喵窝联合银行）操作向导。  
关于NyaaBank插件详情，请见[此页](legacy/nyaa/economics/nyaabank.md "NyaaBank介绍")。

!> **本页需要银行家帮助完善。**  
目前全喵窝仅有三位银行家，仅银行家可执行除 `/nb my` 之外的 NyaaBank 命令。  
『银行家操作』栏目的内容复制自早期 NyaaWiki 存档。如果发现过时之处，请与 Wiki 编者联系。

## 普通玩家操作
### 查询存款及贷款情况
执行命令 `/nb my` ，即可获悉在各个银行的账户状况，包括存款余额、贷款数额。

### 存款和取款
在银行网点，找到有`[BANK]`和`存款业务`字样的木牌，对准其单击右键；随后需在**10秒内**打开聊天框，输入欲存入金额并确认（按回车键）。  
同理，找到`取款业务`木牌，对其右键，即可取款。每次取款从现金扣除木牌上所示“手续费”。

银行每**三十日**结算一次利息。存入不足三十日的，按实际存入天数结息。  
利息**不会**算进本金，直至本息一并取出。

?> :information_source: 作为参考，银行系统曾于 **2020 年 6 月 7 日**结息。

### 贷款与还款
和存款类似，找到有`[BANK]`和`贷款业务`字样的木牌，上面显示最大可贷款额度与利息。对其单击右键以贷款。  
还款时则在`还款业务`木牌办理。

## 银行家操作
这里提供银行相关的操作方法、业务木牌和命令的帮助。银行家执行相关需要银行 ID 的命令时，只能使用自己所拥有的银行 ID，不能使用其他银行的 ID。

请注意，用户与银行的所有资金交互，都是在与银行家的现金帐户交互。因此，请银行家时刻确保自己拥有足够的现金。现金长期不足，影响到玩家正常使用的银行将被强制破产。

### 业务木牌

#### 存款

存款木牌允许玩家右键与木牌交互时将自己所拥有的现金存入对应银行（银行家的现金帐户）。木牌格式：

- 第一行：`[bank]`
- 第二行：金融机构编号，在银行建立时银行家会得到这个编号。例如编号为 `1` 即写 `1`。
- 第三行：`DEPOSIT`
- 第四行：储蓄利率，如果希望储蓄利率为 1.2% 则写 `1.2`。留空即为默认。

一个储蓄业务木牌的样例：

```
    [bank]
       1
    DEPOSIT
      1.0
```

#### 取款

取款木牌允许玩家在右键与木牌交互时从对应银行（银行家的现金帐户）取出自己所拥有的储蓄资金，并支付一定的手续费用（如果有）。取款业务木牌格式如下：

- 第一行：`[bank]`
- 第二行：金融机构编号
- 第三行：`WITHDRAW`
- 第四行：手续费用。例如每次交易手续费用为 1 节操，即写 `1`。改行不可留空，如不需要手续费，请写 `0`。

#### 贷款

贷款木牌允许玩家在右键与木牌交互时得到相应的贷款资金。一个玩家在一个银行同时只能有一笔贷款，在还清当前贷款之前，该玩家不能在此银行再次贷款。银行家需要注意不要设置过多的贷款金额，以免出现资金无法周转的情况。贷款木牌格式如下：

- 第一行：`[bank]`
- 第二行：金融机构编号
- 第三行：`LOAN`
- 第四行：贷款金额，例如该木牌可贷款 1,000 节操则写 `1000`。该行不可留空、不可为零。

#### 还款

还款木牌允许玩家在右键与木牌交互时偿还一定的贷款额度。玩家使用木牌后可选择一次还清或偿还一部分金额。还款木牌格式如下：

- 第一行：`[bank]`
- 第二行：金融机构编号
- 第三行：`REPAY`
- 第四行：交易手续费，该行不可留空，如果不需要手续费，请写 `0`。

### 可用命令

- `/nb bank`
  - `/nb bank info` - 查看银行信息
  - `/nb bank customers` - 查看客户列表
