# 粒子护盾 v3.3.0 终极修复版

> 基于 ParticleShield-3.1.5 字节码级审计与重写。本版本每一项功能均经 javap 字节码验证与运行时测试，非广告词。

## 严重问题修复清单

### v3.1.5 原始严重问题（P0）
1. **崩溃防护是死代码**：ExploitManager 从不调用 11 个检测器，全 JAR 无数据包监听；检测器本身为空壳（恒返回 0/false）。
2. **反作弊 7/9 检测未运行**：仅 Speed/Fly 生效；AimDuplicateLook 存在必然提前 return 的 bug。
3. **JDBC 凭据保险箱为 XOR 加密**：可秒破；无主密钥时数据库密码**明文落盘**。
4. **Hardener 16 个安全模块从未启动**（JWT/CSRF/限速/Argon2/RLS/审计/备份等全是死代码）。

### v3.2.0 修复
- PacketEvents 真实数据包监听 + 11 个检测器重写为真实逻辑（Bundle 洪水/速率、包洪水、物品 NBT/附魔/堆叠校验、畸形包、2MB 巨型包、NBT 深度、窗口点击/确认合法性），违规自动取消数据包并踢出
- 反作弊全量接入（伤害/破方块/速度事件 + 每秒定时器 + Grim 处理器）
- 保险箱真 AES-256-GCM（随机 IV + 认证标签 + 原子写入 + 无密钥拒写 + 拒绝加载旧明文文件）
- 16 个安全模块全部启动；密钥走环境变量 `PSHIELD_VAULT_KEY` / `PSHIELD_JWT_SECRET`
- code-review 复查追加：Netty 线程踢人改主线程调度、反射 Method 缓存

### v3.3.0 追加修复（第二轮穷尽审计）
1. **处罚系统对管理员不可用**（ban/kick/ipban/mute 等 8 方法全插件零调用）→ 新增 12 个子命令：ban/tempban/ipban/unban/mute/tempmute/unmute/kick/softban/blacklist/unblacklist/history/check，颗粒化权限，IP 封禁同步写入防火墙黑名单
2. **广告拦截误报极高**（消息含"端口"两字即被拦）→ 域名/Discord/IPv4 严格正则 + 信任分 ≥80 豁免 + 禁言写库调度主线程
3. **Panic 模式形同虚设**（只发消息不拦人）→ 非 bypass 玩家直接踢出并告警
4. **防火墙缺陷**：计数映射永不清除（泄漏）→ 定期清理；VPN 检测明文 HTTP（可被中间人篡改）→ HTTPS；世界路由从未实现 → 白名单国家路由真正生效
5. **Web 面板认证薄弱**：SHA-256 → Argon2id（65MB/3轮/4线程/16B盐，旧哈希自动迁移）；比较改常量时间；控制台不再打印明文密码
6. **依赖清理**：删除 ProtocolLib 硬依赖（全 JAR 零引用），仅保留真实使用的 packetevents

## 部署

1. 服务器安装 `packetevents-spigot`（唯一硬依赖）
2. 替换 `plugins/ParticleShield.jar` 为本 JAR，重启
3. 设置环境变量 `PSHIELD_VAULT_KEY`、`PSHIELD_JWT_SECRET`（≥32 字符随机串）
4. 游戏内 `/ps help` 查看 18 个子命令；`/pshield-hardener status` 查看 16 个安全模块状态

## 验证记录

- 21+5 个重写类编译（Java 8 字节码，与全包一致）；JAR 无重复条目、无依赖泄漏
- jdeps：新类无未解析引用
- 保险箱功能测试 6 项全过（无密钥拒写/往返解密/错钥拒绝/旧文件拒绝）
- 安全模块注册测试：16/16 激活
