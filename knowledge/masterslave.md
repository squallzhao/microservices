    读写请求由Master负责

    写请求写到Master后，由Master同步到Slave上

    由Master push or Slave pull

    通常是由Slave 周期性来pull，所以是最终一致性

    问题： 若在 pull 周期内（不是期间？），master挂掉，那么会导致这个时间片内的数据丢失
    ------------------------------------------------------------------------------

    若不想让数据丢掉，Slave 只能成为 ReadOnly方式等Master恢复

    若容忍数据丢失，可以让 Slave代替Master工作

    如何保证强一致性？
    ------------------

    Master 写操作，写完成功后，再写 Slave，两者成功后返回成功。若 Slave失败，两种方法

    标记 Slave 不可用报错，并继续服务（等恢复后，再同步Master的数据，多个Slave少了一个而已）

    回滚自己并返回失败
