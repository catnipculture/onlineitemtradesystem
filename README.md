> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

本系统一共管理员，用户角色。

管理员功能有个人中心，用户管理，商品分类管理，品牌管理，商品信息管理，系统管理，订单管理等。

用户可以注册登录购买商品查看订单等。

# 环境要求

1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA;

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS;

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目

6.数据库：MySql5.7/8.0等版本均可；

# 技术栈

运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：SpringBoot + MyBatis + Vue + Bootstrap + jQuery

# 使用说明

1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件；

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目；

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码地址：[http://www.codegym.top](http://www.codegym.top/)



# 运行截图

## 文档截图

![img](https://i-blog.csdnimg.cn/img_convert/022e8545b8157d7b4fe4a4b8b42c3aa3.png)

### 项目截图

前台

![springboot082在线宠物用品交易网站的设计与实现5](https://i-blog.csdnimg.cn/img_convert/b358dfdf0c00131a6dfb212b55d385d5.png)

![springboot082在线宠物用品交易网站的设计与实现8](https://i-blog.csdnimg.cn/img_convert/300fe28758d7f0d5c0d9f04972d62244.png)

![springboot082在线宠物用品交易网站的设计与实现9](https://i-blog.csdnimg.cn/img_convert/a7608cc5956bc1ec22721e878378f7c4.png)

![springboot082在线宠物用品交易网站的设计与实现10](https://i-blog.csdnimg.cn/img_convert/22ab12294704d4c0a08e4f600dc92722.png)

![springboot082在线宠物用品交易网站的设计与实现0](https://i-blog.csdnimg.cn/img_convert/464ac3dd2e538d5df35c678f681e437e.png)

![springboot082在线宠物用品交易网站的设计与实现1](https://i-blog.csdnimg.cn/img_convert/94223ddc77eb9a957f59d59e3b79eced.png)

![springboot082在线宠物用品交易网站的设计与实现2](https://i-blog.csdnimg.cn/img_convert/5f65265475da0f116e440e7c6e04509f.png)

后台

![springboot082在线宠物用品交易网站的设计与实现3](https://i-blog.csdnimg.cn/img_convert/0788a9eb348184c941e98dac9d57fe76.png)

![springboot082在线宠物用品交易网站的设计与实现4](https://i-blog.csdnimg.cn/img_convert/ee2acd600298780162239c978d29979d.png)
### 代码

```
    public void process(JSONObject params) {
        JSONObject data = params.getJSONObject("data");
        CustomerDTO customerDTO = customerCreatedProcessor.getCustomerDTO(data.getJSONObject("userInfo"));
        String telephone = customerDTO.getTelephone();
        if (StringUtils.isEmpty(telephone)) {
            log.error("用户手机号为空，无法登录");
        }
        LambdaQueryWrapper<CustomerDO> queryWrapper = new LambdaQueryWrapper<>();
        queryWrapper.eq(CustomerDO::getTelephone, telephone);
        CustomerDO customerDO = customerMapper.selectOne(queryWrapper);
        customerDO.setNickname(customerDTO.getNickname());
        customerDO.setGender(customerDTO.getGender());
        customerDO.setAddress(customerDTO.getAddress());
        customerDO.setDescription(customerDTO.getDescription());
        customerMapper.updateById(customerDO);
    }
```
