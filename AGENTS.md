# 口哨冒险 (Whistle Platformer)

口哨声控横版关卡障碍通关游戏。Web Audio API 音高检测驱动角色动作。

## 目标平台

| 平台 | 方式 | 产出 |
|------|------|------|
| 🍎 iOS | Capacitor → Xcode | IPA |
| 🤖 Android | Capacitor → Gradle | APK |
| ⌚ 手表 | 窄屏自适应 | 同 APK |
| 👓 智能眼镜 | 窄FOV+语音 | 同 APK |

## 玩法

- 口哨音高控制动作：低音=走/蹲，中音=跳，高音=冲刺
- 横版卷轴关卡，躲避障碍通关
- 多关卡，收集金币
- 👓 智能眼镜：窄FOV自适应 + 语音命令控制（自动检测屏幕尺寸）

### 语音命令（智能眼镜模式）
| 命令 | 映射频率 | 动作 |
|------|----------|------|
| 跳 / 上 / up | 500Hz (mid) | 跳跃 |
| 蹲 / 下 / down | 300Hz (low) | 蹲/走 |
| 冲 / 快 / right | 800Hz (high) | 冲刺 |
| 停 | 0Hz | 停止 |

## 技术栈

- Web Audio API 音高检测
- Canvas 2D 横版渲染
- Capacitor 原生包装
- Web Speech Recognition API（眼镜语音控制）
- DeviceOrientation + DeviceMotion（智能戒指/手杖）

## Harness / Loop（助手）

- 遵循根 `/Users/skat/AGENTS.md`：**Harness Engineering** + **Loop Engineering**
- Guide = 本文件；Sensor = 下方验证命令；同类失误第二次须沉淀规则或测试（棘轮）
- 开干前写清 **Done**；每切片过验证环；显式停止（成功 / 上限 / 无进展 / 人审）
- 详解：`docs/HARNESS_ENGINEERING.md`、`docs/LOOP_ENGINEERING.md`

## 验证环 / Done

```bash
npm install
npm test          # 若有
npm run build     # 或 build:web
npx cap sync android   # 若有 android/
# 可选：JAVA_HOME=…/openjdk@17 npm run apk:debug
```

**Done 示例**：测试通过（若有）+ web 产物进 `www/`/`dist/` + `cap sync` 无报错。可选穿戴未做可搁置，不纳入强制 Done。
