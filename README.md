# SlimeVR_TT.Ver  
<div align=center><img src="https://github.com/TerayTech/SlimeVR_TT.Ver/blob/main/img/IMG_0465.jpg" width="300"></div>  
  
## 1 Intro  
  
### 本项目为SlimeVR开源硬件项目的复制版，兼容ICM-20948/BNO-08x 9轴陀螺仪（可选）,主控为性能更好的ESP32，具有以下特性：  
  
1. 使用更好的充放电管理方案。使用IP2312 DC/DC锂离子电池充电芯片，解决TP4056的巨大发热问题，最大充电电流可到3.1A  
  
2. 增加了一颗HX70A 锂离子电池电量显示IC，单击按钮即可查看当前节点的剩余电量，而不需要通过上位机查看，更加方便  
  
3. 设计了2个带有INT引脚的AUX接口，可用于外挂BNO-08x模块，同时兼容其他型号的陀螺仪模块  
  
4. 使用TPS63070 Buck-Boost IC，对比传统方案所使用的单个LDO，能够将电池寿命发挥至极限，增加追踪器的续航  
  
5. 使用3D打印制作的配套外壳，由@[SteveHawking]完成  
<div align=left><img src="https://github.com/TerayTech/SlimeVR_TT.Ver/blob/main/img/case1.png" width="300"></div>  
<div align=left><img src="https://github.com/TerayTech/SlimeVR_TT.Ver/blob/main/img/case3.jpg" width="300"></div>  
  
## 2 Tips 
1. 推荐所有传感器均使用BNO-085，因为ICM-20948的效果我个人认为没有很好。  
  
2. 有关ICM-20948的价格，供应商报价45/pcs，某宝38/pcs，某鱼30/pcs  
### 警告，不要在淘宝购买99元一个的BNO-085模块，其使用翻新料，具有严重的漂移问题！！  
  
3. 陀螺仪作为MEMS器件，其焊接要求十分高。这里我们要首先说明第一个要注意的点，我们需要避免重复多次焊接陀螺仪芯片。
在博世公司给出的《BNO-055 处理、焊接以及安装说明手册》中提到了：该产品可以承受最多3个回流焊接周期。这可能是一种情况，即PCB安装了来自两侧的设备（即需要2个回流周期），并且在下一个步骤中可能需要额外的重新工作周期（1个回流）  
在实际的测试中，经过三次焊接的IMU-20948芯片其在性能上已经表现出明显异常。如社区中大家所说的“体制”问题，MEMS器件在经过三次焊接流程后，其内部的机械结构已经发生了不可逆转的变化，其获得的数据已经不再可信，解决办法是更换新的传感器芯片。同时，我们应该尽量避免使用拆机翻新的传感器，翻新的传感器也已经经过了2次焊接过程，失效的可能性较大  
  
4. 固件除了修改引脚定义，还对电量算法做了ESP32专门的适配，但是目前处于一个勉强能用的状态。由于原版固件的电量采用分段系数补偿，目前的版本的算法将电池视为理想线性系统，因此电量计算仍不准确，仅可作为参考，我会尽快更新固件。  
  
<div align=center><img src="https://github.com/TerayTech/SlimeVR_TT.Ver/blob/main/img/demo.JPG" width="400"></div>  
<div align=center><img src="https://github.com/TerayTech/SlimeVR_TT.Ver/blob/main/img/IMG_0468.JPG" width="400"></div>  
<div align=center><img src="https://github.com/TerayTech/SlimeVR_TT.Ver/blob/main/img/case2.png" width="400"></div>  
  
