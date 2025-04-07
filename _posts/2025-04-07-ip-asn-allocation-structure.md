---
layout: post
title: "IP和ASN分配机构层级结构"
date: 2025-04-07
categories: [网络]
---

# IP和ASN分配机构层级结构

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

## 说明

1. **IANA (Internet Assigned Numbers Authority)**
   - 负责全球IP地址和AS号码的分配
   - 隶属于ICANN (互联网名称与数字地址分配机构)
   - 官网：https://www.iana.org/
   - WHOIS查询：https://www.iana.org/whois

2. **RIRs (Regional Internet Registries)**
   - 负责各自地理区域的IP地址和AS号码分配
   - 目前有5个RIR：
     - ARIN (北美)
       - 官网：https://www.arin.net/
       - WHOIS查询：https://whois.arin.net/
       - WHOIS服务域名：whois.arin.net
     - RIPE NCC (欧洲、中东和中亚)
       - 官网：https://www.ripe.net/
       - WHOIS查询：https://apps.db.ripe.net/db-web-ui/
       - WHOIS服务域名：whois.ripe.net
     - APNIC (亚太)
       - 官网：https://www.apnic.net/
       - WHOIS查询：https://www.apnic.net/whois-search/
       - WHOIS服务域名：whois.apnic.net
     - LACNIC (拉丁美洲和加勒比海)
       - 官网：https://www.lacnic.net/
       - WHOIS查询：https://www.lacnic.net/whois/
       - WHOIS服务域名：whois.lacnic.net
     - AFRINIC (非洲)
       - 官网：https://www.afrinic.net/
       - WHOIS查询：https://www.afrinic.net/whois
       - WHOIS服务域名：whois.afrinic.net

3. **分配流程**
   - IANA → RIRs → ISPs → 最终用户
   - 每个层级都有相应的分配政策和规则
   - 遵循"先到先得"和"合理使用"原则

4. **AS号码分配**
   - 同样遵循类似的层级结构
   - 由IANA分配给RIRs
   - RIRs再分配给需要AS号码的组织

5. **ISP和IX运营商**
   - **ISP (互联网服务提供商)**
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

   - **IX运营商 (互联网交换中心运营商)**
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

6. **其他重要资源**
   - 全球IP地址分配统计：https://www.iana.org/assignments/ipv4-address-space/ipv4-address-space.xhtml
   - 全球AS号码分配统计：https://www.iana.org/assignments/as-numbers/as-numbers.xhtml
   - 各RIR的IP地址分配政策：可在各RIR官网的"Policies"部分查看

7. **补充数据库和WHOIS服务**
   - **WHOIS服务域名**
     - 官方分配机构：
       - IANA: whois.iana.org (IP和ASN分配)
         - IP查询：`whois -h whois.iana.org 8.8.8.8`
         - ASN查询：`whois -h whois.iana.org AS15169`
       - ARIN: whois.arin.net (IP和ASN分配)
         - IP查询：`whois -h whois.arin.net 8.8.8.8`
         - ASN查询：`whois -h whois.arin.net AS15169`
       - RIPE: whois.ripe.net (IP和ASN分配)
         - IP查询：`whois -h whois.ripe.net 8.8.8.8`
         - ASN查询：`whois -h whois.ripe.net AS15169`
       - APNIC: whois.apnic.net (IP和ASN分配)
         - IP查询：`whois -h whois.apnic.net 8.8.8.8`
         - ASN查询：`whois -h whois.apnic.net AS15169`
       - LACNIC: whois.lacnic.net (IP和ASN分配)
         - IP查询：`whois -h whois.lacnic.net 8.8.8.8`
         - ASN查询：`whois -h whois.lacnic.net AS15169`
       - AFRINIC: whois.afrinic.net (IP和ASN分配)
         - IP查询：`whois -h whois.afrinic.net 8.8.8.8`
         - ASN查询：`whois -h whois.afrinic.net AS15169`
     - 路由注册系统：
       - RADb: whois.radb.net (路由策略)
         - IP查询：`whois -h whois.radb.net 8.8.8.8`
         - ASN查询：`whois -h whois.radb.net AS15169`
       - RIPE IRR: whois.ripe.net (路由策略)
         - IP查询：`whois -h whois.ripe.net 8.8.8.8`
         - ASN查询：`whois -h whois.ripe.net AS15169`
       - ARIN IRR: rr.arin.net (路由策略)
         - IP查询：`whois -h rr.arin.net 8.8.8.8`
         - ASN查询：`whois -h rr.arin.net AS15169`
       - APNIC IRR: whois.apnic.net (路由策略)
         - IP查询：`whois -h whois.apnic.net 8.8.8.8`
         - ASN查询：`whois -h whois.apnic.net AS15169`
       - AFRINIC IRR: whois.afrinic.net (路由策略)
         - IP查询：`whois -h whois.afrinic.net 8.8.8.8`
         - ASN查询：`whois -h whois.afrinic.net AS15169`
       - LACNIC IRR: whois.lacnic.net (路由策略)
         - IP查询：`whois -h whois.lacnic.net 8.8.8.8`
         - ASN查询：`whois -h whois.lacnic.net AS15169`
       - NTTCOM IRR: whois.ntt.net (路由策略)
         - IP查询：`whois -h whois.ntt.net 8.8.8.8`
         - ASN查询：`whois -h whois.ntt.net AS15169`
       - ALTDB: whois.altdb.net (路由策略)
         - IP查询：`whois -h whois.altdb.net 8.8.8.8`
         - ASN查询：`whois -h whois.altdb.net AS15169`
       - LEVEL3: whois.level3.net (路由策略)
         - IP查询：`whois -h whois.level3.net 8.8.8.8`
         - ASN查询：`whois -h whois.level3.net AS15169`
     - 大型ISP和IX运营商：
       - Hurricane Electric: whois.he.net
         - IP查询：`whois -h whois.he.net 8.8.8.8`
         - ASN查询：`whois -h whois.he.net AS15169`
       - PCH: whois.pch.net
         - IP查询：`whois -h whois.pch.net 8.8.8.8`
         - ASN查询：`whois -h whois.pch.net AS15169`
       - Level3/CenturyLink: whois.level3.net
         - IP查询：`whois -h whois.level3.net 8.8.8.8`
         - ASN查询：`whois -h whois.level3.net AS15169`
       - NTT: whois.ntt.net
         - IP查询：`whois -h whois.ntt.net 8.8.8.8`
         - ASN查询：`whois -h whois.ntt.net AS15169`
       - Verisign: whois.verisign-grs.com
         - IP查询：`whois -h whois.verisign-grs.com 8.8.8.8`
         - ASN查询：`whois -h whois.verisign-grs.com AS15169`
     - 安全研究机构：
       - Team Cymru: whois.cymru.com
         - IP查询：`whois -h whois.cymru.com " -v 8.8.8.8"`
         - 批量查询：`whois -h whois.cymru.com " -v 8.8.8.8 1.1.1.1"`
       - RPKI数据库: whois.rpki.net
         - IP查询：`whois -h whois.rpki.net 8.8.8.8`
         - ASN查询：`whois -h whois.rpki.net AS15169`
       - DNS-OARC: whois.dns-oarc.net
         - IP查询：`whois -h whois.dns-oarc.net 8.8.8.8`
         - ASN查询：`whois -h whois.dns-oarc.net AS15169`
     - 其他补充服务：
       - BGPView
         - 网页查询：https://bgpview.io/
       - IPinfo
         - 网页查询：https://ipinfo.io/
       - PeeringDB
         - 网页查询：https://www.peeringdb.com/
       - CAIDA AS Rank
         - 网页查询：https://asrank.caida.org/

   - **官方分配机构**
     - **IANA**
       - 提供全球IP地址和AS号码分配信息
       - 官网：https://www.iana.org/
       - 简述：互联网号码分配机构
       - 所属：ICANN (美国)，互联网名称与数字地址分配机构
       - 权威性：最高级别权威，负责全球IP和AS号码分配
       - WHOIS服务域名：whois.iana.org
       - 特点：
         - 提供全球IP地址空间分配信息
         - 提供AS号码分配信息
         - 数据来源最权威

     - **RIRs (Regional Internet Registries)**
       - 提供区域IP地址和AS号码分配信息
       - 简述：区域互联网注册管理机构
       - 所属：各区域RIR组织
       - 权威性：在各自区域内具有最高权威
       - 包含：
         - ARIN (北美)
         - RIPE NCC (欧洲、中东和中亚)
         - APNIC (亚太)
         - LACNIC (拉丁美洲和加勒比海)
         - AFRINIC (非洲)
       - 特点：
         - 提供区域IP地址分配信息
         - 提供AS号码分配信息
         - 数据由官方维护

   - **路由注册系统**
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

   - **大型ISP和IX运营商**
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

   - **安全研究机构**
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

   - **其他补充服务**
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

8. **注意事项**
   - RIR的WHOIS服务是最权威的来源，但可能不包含所有历史数据
   - 补充数据库通常提供更丰富的元数据和关系信息
   - 不同数据库的更新频率和覆盖范围可能不同
   - 建议交叉验证多个来源的信息 