本系统是点餐系统，包括管理端以及顾客端。
技术栈包含uniapp、JSON、JWT、axios、ruoyi、vue、elementUI、echart、spring、springmvc、springboot、websocket、mysql、mybatis、springsecurity\redis等。
此外，还采用了协同过滤算法。这里最主要采用了皮尔逊相似度进行计算：![image](https://github.com/user-attachments/assets/2f8bbe79-ab7f-4535-8fa4-41acb1e1c6f0)
![image](https://github.com/user-attachments/assets/ea03c5a0-5bc6-4bf5-93e2-f2f4e5f08eb4)

这里还用到了websocket，使得客户和后台之间能进行留言沟通。
系统总体开发架构图如下：
![image](https://github.com/user-attachments/assets/2cc84624-6b63-4c15-ba3e-5dc97caefb43)

管理端主要通过魔改ruoyi的代码。管理端包含菜品管理模块、订单管理模块、红包卡券模块、顾客管理模块、联系客服模块以及报表的查看。
红包卡券管理：
红包卡券主要是通过UUID生成红包兑换码，确保生成的兑换码不存在重复。UUID一般有32位16进制。
![image](https://github.com/user-attachments/assets/7b0d840e-3f6b-4b58-8686-58f2fe47736d)
![image](https://github.com/user-attachments/assets/3b132a58-ef09-4183-be7c-3f3a46091105)
![image](https://github.com/user-attachments/assets/99b59de4-ec99-4a53-844d-acaba2bb9e5c)
![image](https://github.com/user-attachments/assets/514a624e-e9ce-4e55-ba01-e42800636ea1)
![image](https://github.com/user-attachments/assets/9d5946a7-0f8d-4f3b-b835-3053a1f7559a)
菜品管理：
![image](https://github.com/user-attachments/assets/3a8d74e3-d209-4e36-a8aa-04a0d4ca355b)
![image](https://github.com/user-attachments/assets/a13764c3-5aa3-4442-a5aa-f1faebfb00db)
![image](https://github.com/user-attachments/assets/d579ddc5-67b0-477b-a8b7-e9e563f55354)
![image](https://github.com/user-attachments/assets/78bfb11b-4d27-45ae-b93e-5bc7727f15bd)
![image](https://github.com/user-attachments/assets/d1535b92-756b-4c51-adbf-33b94b69b202)
![image](https://github.com/user-attachments/assets/bc761a61-7f22-4b6b-bd29-4c216225568e)
![image](https://github.com/user-attachments/assets/6730c0e1-a74a-4cea-83ef-a2304cdd6977)

订单管理：
![image](https://github.com/user-attachments/assets/6f593656-f63e-479d-9a03-1722ac4a9019)
![image](https://github.com/user-attachments/assets/4979ab17-e771-4016-abde-0c76cab696b7)
![image](https://github.com/user-attachments/assets/70535b25-84fa-4e58-ae78-f5c0e744f109)
![image](https://github.com/user-attachments/assets/f1c2bcba-9df1-4fbe-89d1-8d9183d82e09)

顾客管理：
可以封禁客户，让其无法登录顾客前端系统。
![image](https://github.com/user-attachments/assets/b73c0a19-73a3-479e-938b-731ba827fee9)
![image](https://github.com/user-attachments/assets/9c8b1b56-5aa3-4ae6-adde-6c1c9b8e3ed5)
![image](https://github.com/user-attachments/assets/128ed404-769b-4b26-8814-ffd6aa1ed379)
![image](https://github.com/user-attachments/assets/68f6dbf0-f90e-4a5b-9af9-a982b58111de)

联系客服模块：
使用者在前端通过与服务器建立WebSocket长链接，之后就可以通过这一链接进行实时对话，而实时对话的聊天格式还是采用JSON进行交互。管理员端与每一个餐桌的聊天记录都会存在本地的SessionStorage存储中，每次选择某一餐桌的客户时，都会自动显示与其之前的对话内容到聊天框之中。客户的聊天记录也会每次都存储在本地的SessionStorage存储之中，下次再次打开这一界面时，会自动弹出与后台服务员的所有对话内容。后端的数据传送以及方法调用仍然采用Model层的实体类进行必要的封装。

![image](https://github.com/user-attachments/assets/cbb4836c-7a8f-450b-9a63-6b4e72b6fad1)
报表模块：
主要还是使用了Echart进行描绘
![image](https://github.com/user-attachments/assets/4a2f0ff4-bbc4-425e-ab6b-e95d2f55ee35)

顾客端主要包括：登录注册、菜单分类展示、菜品展示、扫码下座、下单点餐、规格选取、优惠减免、支付订单、评分评价、联系客服等。
登录注册：

![image](https://github.com/user-attachments/assets/6b8de02a-2ead-4a33-8b13-418f5be0e8d3)
![image](https://github.com/user-attachments/assets/238df64f-1063-4f40-b139-d1f3f075d4b4)
![image](https://github.com/user-attachments/assets/11f6cc4c-4db8-42e6-baf9-f39b86cdd25a)

菜单展示以及点餐模块：
可以随意生成二维码，二维码里面包括桌号的json，然后小程序扫码后，可以查看到里面的包含桌号的json。
![image](https://github.com/user-attachments/assets/b54dd361-bc96-417a-a6e8-a13ac95db47e)
![image](https://github.com/user-attachments/assets/a9d5c302-27cc-4e52-acc1-73b346540df0)
![image](https://github.com/user-attachments/assets/3afb3e64-8377-4e62-adc3-37db4add8ebe)
![image](https://github.com/user-attachments/assets/88182fe3-333b-4c56-a70a-66af5a1ed899)
![image](https://github.com/user-attachments/assets/16a738ee-22a7-407e-aa6c-969fe8253df5)
![image](https://github.com/user-attachments/assets/77f50c24-cba7-4928-bba1-8119e435a9a9)
![image](https://github.com/user-attachments/assets/03bd658f-5063-4b6e-9b45-aa1155af5545)
![image](https://github.com/user-attachments/assets/b00295e3-f2b7-40e9-b44b-c25cc01851df)
![image](https://github.com/user-attachments/assets/dd6f4d29-5133-4b00-8cc6-b7da75aa82c3)
![image](https://github.com/user-attachments/assets/8054e12c-236b-4de6-b7d9-d99e754e6da9)
![image](https://github.com/user-attachments/assets/d6363e63-5613-4a01-a7f8-03cc489cde24)

订单模块：
![image](https://github.com/user-attachments/assets/5b755957-4a12-4296-8276-54e827181ebe)
![image](https://github.com/user-attachments/assets/e9879ca7-77b6-40d6-92fc-53699e8ccc5b)
![image](https://github.com/user-attachments/assets/117e7c71-356e-42a2-9b23-9df2c0c8e045)

评价模块：
![image](https://github.com/user-attachments/assets/a447e2b9-0cee-44a9-8b86-e681d5906700)
![image](https://github.com/user-attachments/assets/2180c368-a083-41cf-be2c-4c077cc3154a)
![image](https://github.com/user-attachments/assets/205a7069-78f0-4df6-8f1e-96b7c89cc42e)
![image](https://github.com/user-attachments/assets/ccb2fb09-e5d3-45bb-9002-5e7e04a99940)
![image](https://github.com/user-attachments/assets/052c620d-e2d0-4df3-a837-58298f412610)
![image](https://github.com/user-attachments/assets/fa6793d9-cc52-4d25-99ad-0758b5ef613a)

资料修改模块：
![image](https://github.com/user-attachments/assets/ce8ed131-fc29-4f15-a549-d6a6ab46a00f)
![image](https://github.com/user-attachments/assets/e668587f-efbb-417e-b8f9-3c222682a490)
![image](https://github.com/user-attachments/assets/6f8b8e0e-c103-43a9-a72a-bca209da686d)
![image](https://github.com/user-attachments/assets/5ebbb859-bec7-4083-bfc3-df6659b90eb0)

红包卡券模块：
红包会有过期红包和可使用红包。过期红包会根据服务器的时间进行判断，若超过当前服务器时间则判断为过期红包，那么在顾客端就用不了。
可使用红包包括无门槛红包和有门槛优惠券。这里的无门槛红包可能使用时候会超过使用的金额，例如你购买18元的东西，想使用20元的红包。这时结算时会为-2元。那这种情况显然不行，那么我们就应该要补充多一个if来判断这种情况，如果是-数的，那么直接付款为0即可。
而有门槛红包则需要先加个if判断当前金额是否超过当前的门槛金额，才可以使用。
![image](https://github.com/user-attachments/assets/96180656-3602-49f9-9555-d41cf898cb21)
![image](https://github.com/user-attachments/assets/a0427724-134d-40d6-b00a-36867623a28b)
![image](https://github.com/user-attachments/assets/dfd0f29f-78c6-442c-9ff7-41d9f6f42417)
![image](https://github.com/user-attachments/assets/26fa12c7-f1aa-4fda-a680-a5af30e4ba41)
![image](https://github.com/user-attachments/assets/a0c2bda1-8a42-4f89-be71-09da98928396)
![image](https://github.com/user-attachments/assets/86ff755a-b61c-46cd-ad36-ca915ab02143)
![image](https://github.com/user-attachments/assets/f1fa916f-d57e-44f6-876d-d0aaab33830a)
![image](https://github.com/user-attachments/assets/abdc00bd-a821-4741-acb5-b02b774a76bb)

扫桌号模块：
![image](https://github.com/user-attachments/assets/6f81721b-22fd-47fe-8034-2b0f98a98dcb)
![image](https://github.com/user-attachments/assets/ebfd7b49-ac23-472e-9cc5-f3923e9d22b0)
![image](https://github.com/user-attachments/assets/abe239a8-ae60-4595-b47d-0a1ca55e0156)
