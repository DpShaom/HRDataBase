# 命名规约

## 目录
<span id="qj">全局</span>
<span id="bl">变量命名</span>
<span id="fwc">服务层</span>
<span id="hxc">核心层</span>
<span id="mmfsm">命名法说明</span>


## 全局
[ ](#qj)
1. 标识符的命名要清晰、明了，有明确含义，同时使用完整的单词或大家基本可以理解的缩写，避免使人产生误解——尽量采用采用英文单词或全部中文全拼表示，若出现英文单词和中文混合定义时，使用连字符“_”将英文与中文割开。较短的单词可通过去掉“元音”形成缩写；较长的单词可取单词的头几个字母形成缩写；一些单词有大家公认的缩写。例如：temp->tmp、flag->标志寄存器、statistic->stat、increment->inc、message->msg等缩写能够被大家基本认可。
2. 命名中若使用特殊约定或缩写，则要有注释说明。应该在源文件的开始之处，对文件中所使用的缩写或约定，特别是特殊的缩写，进行必要的注释说明。
3. 自己特有的命名风格，要自始至终保持一致，不可来回变化。个人的命名风格，在符合所在项目组或产品组的命名规则的前提下，才可使用。(即命名规则中没有规定到的地方才可有个人命名风格)。
4. 对于变量命名，禁止取单个字符(如i 、j 、k... )，建议除了要有具体含义外，还能表明其变量类型、数据类型等，但i 、j 、k 作局部循环或lambda变量是允许的。变量，尤其是局部变量，如果用单个字符表示，很容易敲错(如i写成j)，而编译时又检查不出来，有可能为了这个小小的错误而花费大量的查错时间。
5. 除非必要，不要用数字或较奇怪的字符来定义标识符。
6. 命名规范必须与所使用的系统风格保持一致，并在同一项目中统一。
7. 在同一软件产品内，应规划好接口部分标识符(变量、结构、函数及常量)的命名，防止编译、链接时产生冲突。对接口部分的标识符应该有更严格限制，防止冲突。如可规定接口部分的变量与常量之前加上“模块”标识等。
8. 用正确的反义词组命名具有互斥意义的变量或相反操作的函数等。如
>add / remove  
>begin / end   
>create / destroy  
>insert / delete  
>first / last  
>get / release  
>increment / decrement  
>put / get

## 变量命名
[ ](#bl)
1. 变量的命名规则要求用“帕斯卡命名”。
使用英文单词、中文全拼或中文全拼的缩写,要求单词的第一个字母应大写。
2. 常量类要求在帕斯卡命名法的前提前加入C_，如
```C#
    public const string C_FileName;
```


## 服务层（Application）
[ ](#fwc)
### 实体类为单元的服务
采用EntityAppService的形式命名，符合Abp的命名规范，采用帕斯卡命名法，接口I+EntityAppService,Entity首字母一样需要大写。举例如下：

```C#
    public class ProductAppService : BaseHRDataBaseAppService, IProductAppService
    {
        //服务内容实现
    }

    public interface IProductAppService : IApplicationService
    {
        //接口声明        
    }
```

### 工具类方法的命名
采用说NameAppService的形式命名，采用帕斯卡命名法。举例如下：
```C#
    public class CommonAppService : BaseHRDataBaseAppService, ICommonAppService
    {
        //服务内容实现
    }

    public interface ICommonAppService : IApplicationService
    {
        //接口声明        
    }
```
### Dto类
#### 返回结果或视图类
采用帕斯卡命名法，举例如下
```C#
    public class ProductMap
    {
        /// <summary>
        /// 关系映射ID
        /// </summary>
        public int Id { get; set; }
        /// <summary>
        /// 栏目编号
        /// </summary>
        public string MenuID { get; set; }
        /// <summary>
        /// 产品编号
        /// </summary>
        public int Product_ID { get; set; }
        /// <summary>
        /// 产品父级编号
        /// </summary>
        public int ParentID { get; set; }
        /// <summary>
        /// 产品名称
        /// </summary>
        public string Name { get; set; }
    }
```
#### 参数据类
类名采用帕斯卡命名法，属性采用下划线命名法，举例如下
```C#
    public class GuestFilter : BaseFilter
    {
        /// <summary>
        /// 企业ID
        /// </summary>
        public int customer_id { get; set; }
        /// <summary>
        /// 创建者ID
        /// </summary>
        public int create_id { get; set; }
        /// <summary>
        /// 参会类型
        /// </summary>
        public string meeting_types { get; set; }
        /// <summary>
        /// 联系人ID
        /// </summary>
        public int guest_id { get; set; }
```

## 核心层（Core）
[ ](#hxc)
### 表实体类命名
采用帕斯卡命名法，举例如下
```C#
    public class Rcpt_Guests : Entity<int>
    {
        /// <summary>
        /// Id
        /// </summary>
        [Key]
        [Column("Guest_ID")]
        public override int Id { get; set; }

        /// <summary>
        /// 组织Id
        /// </summary>
        public int Organizate_ID { get; set; }
        /// <summary>
        /// 客户（公司）Id
        /// </summary>
        public int CustomerID { get; set; }
        /// <summary>
        /// 联系人Id
        /// </summary>
        public int LinkID { get; set; }
        /// <summary>
        /// 联系人姓名
        /// </summary>
        public string LinkName { get; set; }
        /// <summary>
        /// 性别
        /// </summary>
        public string Sex { get; set; }
        /// <summary>
        /// 手机
        /// </summary>
        public string MobilePhone { get; set; }
        /// <summary>
        /// QQ
        /// </summary>
        public string QQ { get; set; }
        /// <summary>
        /// 电子邮箱
        /// </summary>
        public string Email { get; set; }
        /// <summary>
        /// 职业
        /// </summary>
        public string Duty { get; set; }
        /// <summary>
        /// 是否订了酒店
        /// </summary>
        public bool IsRoom { get; set; }
        /// <summary>
        /// 房间号
        /// </summary>
        public string Room_Num { get; set; }
        /// <summary>
        /// 会议Id
        /// </summary>
        public int Meeting_ID { get; set; }
        /// <summary>
        /// 会务费Id
        /// </summary>
        public int Meeting_ItemID { get; set; }
        /// <summary>
        /// 排序字段
        /// </summary>
        public int? Ord { get; set; }
        /// <summary>
        /// 是否签到
        /// </summary>
        public bool IsSign { get; set; }
        /// <summary>
        /// 是否打印
        /// </summary>
        public bool IsPrint { get; set; }
        /// <summary>
        /// 创建者Id
        /// </summary>
        public int CreateUserID { get; set; }
        /// <summary>
        /// 记录创建时间
        /// </summary>
        public DateTime CreateDate { get; set; }
        /// <summary>
        /// 记录修改者Id
        /// </summary>
        public int? ModifyUserID { get; set; }
        /// <summary>
        /// 记录修改时间
        /// </summary>
        public DateTime ModifyDate { get; set; }
        /// <summary>
        /// 是否删除
        /// </summary>
        public bool IsDeleted { get; set; } = false;
        /// <summary>
        /// 公司电话（参会名录中修改公司电话后会保存到这里）
        /// </summary>
        public string Telephone { get; set; }
    }
```

## 命名法说明
[ ](#mmfsm)
### 帕斯卡命名法
1. 帕斯卡命名法指当变量名和函式名称是由二个或二个以上单词连结在一起，每个单词首字母大写。而构成的唯一识别字时，用以增加变量和函式的可读性。
### 下划线法命名
1. 单词以 ‘_’ 下划线连接，常见文件名的命名。示例：user_name
