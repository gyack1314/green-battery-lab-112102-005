# 原始资料约定

blocks/*.bin 为 little-endian int16 交错样本，manifest 的 sha256/crc32 检查原始字节。firmware.jsonl 的 channels/scale/offset 按位置定义物理量。电流正充负放，电压V、电流A、温度摄氏度，dt_seconds相对块起点。
bench_events.jsonl：kind=start/discharge_start/discharge_end/reset/resume/calibration；resume.ref 指向 reset。reached_cutoff 只在 discharge_end 有意义，完整容量用相邻实际样本梯形积分Ah；不允许跨缺失时间窗插值。
assembly.jsonl 是左闭右开安装期间；modules.csv 定义生产批和化学体系。cohorts.jsonl 定义 request/side/modules/temperature_min/temperature_max/protocol，属于同一 request 两侧不可复用物理模组。
字典未写revision为1；同dictionary的修订可对历史块解释生效，observed_at为获知时刻。块有独立身份，收到同一块不增加循环。

所有名称与数值均为本地合成数据，不代表真实企业、监管结论或生态调查。data/catalog.json 保存文件哈希、原始行数与列；data/updates/ 为后到修订资料，可独立接收。JSON null 表示尚无该值，不与数值零等同；CSV保留原字符串，金额和数量应按十进制解释。来源身份相同且内容相同的重送不产生新业务事实，同身份版本不同内容需保留争议，除明确替代关系外不按到达顺序判定权威。
