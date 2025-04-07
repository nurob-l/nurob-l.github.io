---
layout: post
title: "互联网资源分配与查询：IP、ASN及WHOIS服务详解"
date: 2025-04-07
categories: [网络]
---

# 互联网资源分配与查询：IP、ASN及WHOIS服务详解

<div class="mermaid">
graph TD
    IANA[IANA<br>互联网号码分配机构] --> RIRs[区域互联网注册管理机构 RIRs]
    
    RIRs --> ARIN[ARIN<br>北美地区]
    RIRs --> RIPE[RIPE NCC<br>欧洲、中东和中亚]
    RIRs --> APNIC[APNIC<br>亚太地区]
    RIRs --> LACNIC[LACNIC<br>拉丁美洲和加勒比海]
    RIRs --> AFRINIC[AFRINIC<br>非洲地区]
    
    ARIN --> ISPs[互联网服务提供商]
    RIPE --> ISPs
    APNIC --> ISPs
    LACNIC --> ISPs
    AFRINIC --> ISPs
    
    ISPs --> EndUsers[最终用户]
    
    classDef org fill:#f9f,stroke:#333,stroke-width:2px;
    class IANA,RIRs,ARIN,RIPE,APNIC,LACNIC,AFRINIC org;
</div>

## 目录

1. [互联网资源分配体系](#1-互联网资源分配体系)
2. [WHOIS服务详解](#2-whois服务详解)
3. [查询命令参考](#3-查询命令参考)
4. [注意事项](#4-注意事项)

## 1. 互联网资源分配体系

### 1.1 IANA (Internet Assigned Numbers Authority)
- 负责全球IP地址和AS号码的分配
- 隶属于ICANN (互联网名称与数字地址分配机构)
- 官网：https://www.iana.org/
- WHOIS查询：https://www.iana.org/whois

### 1.2 RIRs (Regional Internet Registries)
- 负责各自地理区域的IP地址和AS号码分配
- 目前有5个RIR：

| RIR名称 | 覆盖区域 | 官网 | WHOIS查询 | WHOIS服务域名 |
|---------|---------|------|-----------|--------------|
| ARIN | 北美 | https://www.arin.net/ | https://whois.arin.net/ | whois.arin.net |
| RIPE NCC | 欧洲、中东和中亚 | https://www.ripe.net/ | https://apps.db.ripe.net/db-web-ui/ | whois.ripe.net |
| APNIC | 亚太 | https://www.apnic.net/ | https://www.apnic.net/whois-search/ | whois.apnic.net |
| LACNIC | 拉丁美洲和加勒比海 | https://www.lacnic.net/ | https://www.lacnic.net/whois/ | whois.lacnic.net |
| AFRINIC | 非洲 | https://www.afrinic.net/ | https://www.afrinic.net/whois | whois.afrinic.net |

### 1.3 分配流程
- IANA → RIRs → ISPs → 最终用户
- 遵循"先到先得"和"合理使用"原则
- 每个层级都有相应的分配政策和规则

### 1.4 AS号码分配
- 同样遵循类似的层级结构
- 由IANA分配给RIRs
- RIRs再分配给需要AS号码的组织

### 1.5 ISP和IX运营商

#### ISP (互联网服务提供商)
- 定义：提供互联网接入服务的组织
- 主要职责：
  - 为最终用户提供互联网接入
  - 运营自己的网络基础设施
  - 管理IP地址和AS号码
- 层级：
  - Tier 1 ISP：拥有全球骨干网络，与其他Tier 1 ISP直接对等互联
  - Tier 2 ISP：区域性或国家级ISP，需要向Tier 1购买传输服务
  - Tier 3 ISP：本地ISP，主要服务最终用户
- 特点：
  - 需要从RIR获取IP地址和AS号码
  - 运营自己的网络基础设施
  - 提供互联网接入服务

#### IX运营商 (互联网交换中心运营商)
- 定义：运营互联网交换中心的组织
- 主要职责：
  - 提供网络互联的物理设施
  - 管理交换中心的运营
  - 促进网络之间的对等互联
- 特点：
  - 提供中立的网络交换环境
  - 降低网络互联成本
  - 提高网络性能
- 重要性：
  - 促进网络互联
  - 优化网络流量
  - 降低网络运营成本

### 1.6 其他重要资源
- 全球IP地址分配统计：https://www.iana.org/assignments/ipv4-address-space/ipv4-address-space.xhtml
- 全球AS号码分配统计：https://www.iana.org/assignments/as-numbers/as-numbers.xhtml
- 各RIR的IP地址分配政策：可在各RIR官网的"Policies"部分查看

## 2. WHOIS服务详解

### 2.1 服务分类与WHOIS域名列表

| 类别 | 机构 | WHOIS服务域名 | 主要用途 |
|------|------|--------------|---------|
| **官方分配机构** | IANA | whois.iana.org | IP和ASN分配 |
| | ARIN | whois.arin.net | IP和ASN分配 |
| | RIPE NCC | whois.ripe.net | IP和ASN分配 |
| | APNIC | whois.apnic.net | IP和ASN分配 |
| | LACNIC | whois.lacnic.net | IP和ASN分配 |
| | AFRINIC | whois.afrinic.net | IP和ASN分配 |
| **路由注册系统** | RADb | whois.radb.net | 路由策略 |
| | RIPE IRR | whois.ripe.net | 路由策略 |
| | ARIN IRR | rr.arin.net | 路由策略 |
| | NTTCOM IRR | whois.ntt.net | 路由策略 |
| | ALTDB | whois.altdb.net | 路由策略 |
| | LEVEL3 | whois.level3.net | 路由策略 |
| **大型ISP和IX运营商** | Hurricane Electric | whois.he.net | BGP路由信息 |
| | PCH | whois.pch.net | IX和DNS信息 |
| | Level3/CenturyLink | whois.level3.net | 骨干网络信息 |
| | NTT | whois.ntt.net | 网络路由信息 |
| | Verisign | whois.verisign-grs.com | 域名和基础设施 |
| **安全研究机构** | Team Cymru | whois.cymru.com | IP到ASN映射 |
| | RPKI | whois.rpki.net | 路由安全认证 |
| | DNS-OARC | whois.dns-oarc.net | DNS运营数据 |

### 2.2 服务详细说明

#### 官方分配机构
- **IANA**
  - 权威性：最高级别权威
  - 特点：
    - 提供全球IP地址空间分配信息
    - 提供AS号码分配信息
    - 数据来源最权威

- **RIRs**
  - 权威性：在各自区域内具有最高权威
  - 特点：
    - 提供区域IP地址分配信息
    - 提供AS号码分配信息
    - 数据由官方维护

#### 路由注册系统
- **IRR (Internet Routing Registry)**
  - 提供路由策略和过滤规则信息
  - 简述：全球分布式路由信息数据库系统
  - 所属：分布式系统，由各RIR和独立IRR共同维护
  - 权威性：各区域性IRR成员具有其管辖范围内的权威性
  - 特点：
    - 提供路由策略信息
    - 提供过滤规则
    - 数据由网络运营商维护

- **RADb (Route Aggregation Database)**
  - 提供路由策略数据库
  - 官网：https://www.radb.net/
  - 简述：最大的公共路由注册数据库之一
  - 所属：Merit Network Inc. (美国)，非营利研究机构
  - 权威性：IRR体系的重要成员，具有较高可信度
  - WHOIS服务域名：whois.radb.net
  - 特点：
    - 提供路由策略信息
    - 提供过滤规则
    - 数据由网络运营商维护

#### 大型ISP和IX运营商
- **Hurricane Electric**
  - 提供全球BGP路由和网络设施信息
  - 官网：https://bgp.he.net/
  - 简述：全球最大的IPv6骨干网络运营商之一
  - 所属：Hurricane Electric (美国)，全球性ISP和IX运营商
  - 权威性：基于自身全球骨干网络的数据，具有较高参考价值
  - WHOIS服务域名：whois.he.net
  - 特点：
    - 提供全球BGP路由视图
    - 提供详细的AS互联信息
    - 数据基于实际网络运营

- **PCH (Packet Clearing House)**
  - 提供全球IX和DNS基础设施信息
  - 官网：https://www.pch.net/
  - 简述：全球互联网交换中心研究和运营机构
  - 所属：PCH (美国)，非营利互联网基础设施运营机构
  - 权威性：运营多个全球IX节点，数据来自实际运营
  - WHOIS服务域名：whois.pch.net
  - 特点：
    - 提供IX节点路由信息
    - 提供DNS根服务器运营数据
    - 全球互联网交换中心数据

- **Level3/CenturyLink**
  - 提供全球骨干网络路由信息
  - 官网：https://www.centurylink.com/
  - 简述：全球主要ISP和骨干网络运营商
  - 所属：CenturyLink (美国)，全球性电信和网络服务提供商
  - 权威性：基于其全球骨干网络运营数据，具有较高参考价值
  - WHOIS服务域名：whois.level3.net
  - 特点：
    - 提供全球骨干网络路由视图
    - 提供详细的AS互联信息
    - 数据基于实际网络运营

- **NTT**
  - 提供全球网络路由和互联信息
  - 官网：https://www.ntt.com/
  - 简述：全球主要ISP和网络服务提供商
  - 所属：NTT Communications (日本)，全球性电信和网络服务提供商
  - 权威性：基于其全球网络运营数据，具有较高参考价值
  - WHOIS服务域名：whois.ntt.net
  - 特点：
    - 提供亚太地区网络路由信息
    - 提供全球网络互联数据
    - 数据更新及时

- **Verisign**
  - 提供域名和网络基础设施信息
  - 官网：https://www.verisign.com/
  - 简述：全球域名和互联网基础设施服务提供商
  - 所属：Verisign (美国)，互联网基础设施服务公司
  - 权威性：作为.com和.net顶级域名的注册管理机构，具有较高权威性
  - WHOIS服务域名：whois.verisign-grs.com
  - 特点：
    - 提供域名注册信息
    - 提供网络基础设施数据
    - 数据来源权威可靠

#### 安全研究机构
- **Team Cymru**
  - 提供IP到ASN的映射服务
  - 官网：https://team-cymru.com/
  - 简述：专注于互联网安全研究的非营利组织
  - 所属：Team Cymru Research NFP (美国)，非营利安全研究机构
  - 权威性：数据来自多个来源的综合，提供快速批量查询能力
  - WHOIS服务域名：whois.cymru.com
  - 特点：
    - 提供高效的IP到ASN的批量查询服务
    - 支持IPv4和IPv6地址查询
    - 提供ASN的所有者信息和地理位置
    - 数据更新频率高

- **RPKI数据库**
  - 提供资源公钥基础设施数据
  - 官网：https://www.rpki.net/
  - 简述：互联网路由安全认证系统
  - 所属：由多个RIR共同维护的分布式系统
  - 权威性：作为路由源认证系统，具有最高级别的权威性
  - WHOIS服务域名：whois.rpki.net
  - 特点：
    - 提供路由源认证信息
    - 提供ASN和IP前缀的合法性验证
    - 数据由RIR直接维护

- **DNS-OARC**
  - 提供DNS和根服务器运营数据
  - 官网：https://www.dns-oarc.net/
  - 简述：DNS运营、分析和研究联盟
  - 所属：DNS-OARC (美国)，非营利DNS研究机构
  - 权威性：由主要DNS运营商和研究机构组成，具有较高权威性
  - WHOIS服务域名：whois.dns-oarc.net
  - 特点：
    - 提供DNS运营数据
    - 提供根服务器统计信息
    - 全球DNS基础设施分析

#### 其他补充服务
- **BGPView**
  - 提供全球BGP路由和ASN信息
  - 官网：https://bgpview.io/
  - 简述：第三方BGP数据聚合平台，非官方组织
  - 所属：由Workonline Communications (南非) 开发和维护
  - 权威性：数据来源于公共BGP数据，非权威信息源，但更新及时
  - 特点：提供ASN的详细信息、前缀、邻居关系等

- **IPinfo**
  - 提供IP和ASN的详细信息
  - 官网：https://ipinfo.io/
  - 简述：商业IP地理位置和情报服务提供商
  - 所属：IPinfo.io (美国)，独立商业公司
  - 权威性：数据来自多个来源的综合，非权威信息源
  - 特点：提供丰富的IP和ASN元数据

- **PeeringDB**
  - 互联网交换点和网络互连信息数据库
  - 官网：https://www.peeringdb.com/
  - 简述：非营利组织维护的网络对等互连数据库
  - 所属：PeeringDB (美国)，注册非营利组织
  - 权威性：行业公认的对等互连信息源，数据由网络运营商自行维护
  - 特点：提供网络互连、对等关系等详细信息

- **CAIDA AS Rank**
  - 提供ASN的排名和关系分析
  - 官网：https://asrank.caida.org/
  - 简述：互联网数据分析研究组织CAIDA开发的AS排名系统
  - 所属：CAIDA (美国)，加州大学圣地亚哥分校互联网数据分析中心
  - 权威性：学术研究机构发布的分析数据，具有较高的学术参考价值
  - 特点：提供ASN的拓扑结构和重要性分析

## 3. 查询命令参考

### 3.1 命令格式总览

| 服务类型 | 查询类型 | 命令格式 | 示例 |
|---------|---------|----------|------|
| 标准WHOIS | IP查询 | `whois -h [hostname] [IP地址]` | `whois -h whois.arin.net 8.8.8.8` |
| | ASN查询 | `whois -h [hostname] AS[AS号码]` | `whois -h whois.arin.net AS15169` |
| Team Cymru | 单IP查询 | `whois -h whois.cymru.com " -v [IP]"` | `whois -h whois.cymru.com " -v 8.8.8.8"` |
| | 批量查询 | `whois -h whois.cymru.com " -v [IP1] [IP2]"` | `whois -h whois.cymru.com " -v 8.8.8.8 1.1.1.1"` |

### 3.2 Web查询服务

| 服务名称 | 用途 | 网址 |
|---------|------|------|
| BGPView | BGP路由和ASN信息 | https://bgpview.io/ |
| IPinfo | IP和ASN元数据 | https://ipinfo.io/ |
| PeeringDB | 网络互连信息 | https://www.peeringdb.com/ |
| CAIDA AS Rank | AS排名和关系分析 | https://asrank.caida.org/ |

### 3.3 查询建议
- 优先使用对应区域的RIR WHOIS服务
- 对于批量查询，推荐使用Team Cymru服务
- 需要详细路由信息时，可使用Hurricane Electric或BGPView
- 需要互连关系信息时，推荐使用PeeringDB

## 4. 注意事项

- RIR的WHOIS服务是最权威的来源，但可能不包含所有历史数据
- 补充数据库通常提供更丰富的元数据和关系信息
- 不同数据库的更新频率和覆盖范围可能不同
- 建议交叉验证多个来源的信息
- 对于亚太地区IP，优先使用APNIC WHOIS服务
- Team Cymru查询需要特殊格式，注意引号和-v参数的使用 