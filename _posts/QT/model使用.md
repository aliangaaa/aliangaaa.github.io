model中数据存储用list、vector快速，用set、map存储大量数据时会卡顿

model中插入数据只需两步，插入一个新行，列表数据更新（data函数会自动处理列表）

进一步加快速度，qlistview->setUniformItemSizes(true)  // 不计算高度
