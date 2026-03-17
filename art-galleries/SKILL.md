---
name: "art-galleries"
description: "Find nearby art galleries. Invoke when user asks for galleries near me."
---

# Nearby Art Galleries

用途
- 提供用户当前位置附近的 Art Galleries 列表
- 统一返回字段与查询行为，便于前端/接口复用

触发条件
- 用户询问“美术馆/画廊 附近 / art galleries near me / nearby galleries”

输入参数
- location: 经纬度 { lat, lng }，必填
- radius_meters: 查询半径，默认 4000
- limit: 返回数量上限，默认 20，最大 50
- filters: 可选筛选（主题类型、评分、是否开放等）

响应字段
- 统一参见 [STANDARD_RESPONSE.md](file:///Users/mac_lkm/workspace/trae/100fj/.trae/skills/STANDARD_RESPONSE.md)
- 本技能 category 固定为 "art-galleries"

错误码
- INVALID_LOCATION: 经纬度不合法
- RADIUS_TOO_LARGE: 超过最大查询半径
- PROVIDER_UNAVAILABLE: 数据源不可用
- RATE_LIMITED: 触发速率限制

示例
- 输入: { location: { lat: 30.123, lng: 120.456 }, radius_meters: 3000, limit: 10 }
- 输出: 标准 POI 列表（见 STANDARD_RESPONSE.md）

隐私与速率限制
- 仅在用户授权定位后查询
- 避免保留精确坐标，必要时进行网格化模糊处理
