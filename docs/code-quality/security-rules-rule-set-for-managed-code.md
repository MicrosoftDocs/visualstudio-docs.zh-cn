---
title: 托管代码的“安全规则”规则集
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 49fe666884c3a96a5c8eb632308e7f732150805e
ms.sourcegitcommit: 9a5cf730d8e43eed6eba25369b7b44cae0b26b98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75929228"
---
# <a name="security-rules-rule-set-for-managed-code"></a>托管代码的“安全规则”规则集

使用 Microsoft 安全规则规则集进行旧代码分析以最大程度地提高报告的潜在安全问题的数量。

|规则|描述|
|----------|-----------------|
|[CA2100](../code-quality/ca2100.md)|检查 SQL 查询是否存在安全漏洞|
|[CA2102](../code-quality/ca2102.md)|在常规处理程序中捕捉非 CLSCompliant 异常|
|[CA2103](../code-quality/ca2103.md)|检查命令性安全|
|[CA2104](../code-quality/ca2104.md)|不要声明只读可变引用类型|
|[CA2105](../code-quality/ca2105.md)|数组字段不应为只读|
|[CA2106](../code-quality/ca2106.md)|保护断言|
|[CA2107](../code-quality/ca2107.md)|检查 deny 权限和 permit only 权限的使用情况|
|[CA2108](../code-quality/ca2108.md)|检查有关值类型的声明性安全|
|[CA2109](../code-quality/ca2109.md)|检查可见的事件处理程序|
|[CA2111](../code-quality/ca2111.md)|指针应为不可见|
|[CA2112](../code-quality/ca2112.md)|受保护的类型不应公开字段|
|[CA2114](../code-quality/ca2114.md)|方法安全性应是类型安全性的超集|
|[CA2115](../code-quality/ca2115.md)|使用本机资源时调用 GC.KeepAlive|
|[CA2116](../code-quality/ca2116.md)|APTCA 方法应只调用 APTCA 方法|
|[CA2117](../code-quality/ca2117.md)|APTCA 类型应只扩展 APTCA 基类型|
|[CA2118](../code-quality/ca2118.md)|检查 SuppressUnmanagedCodeSecurityAttribute 用法|
|[CA2119](../code-quality/ca2119.md)|密封满足私有接口的方法|
|[CA2120](../code-quality/ca2120.md)|保护序列化构造函数|
|[CA2121](../code-quality/ca2121.md)|静态构造函数应为私有|
|[CA2122](../code-quality/ca2122.md)|不要使用链接请求间接公开方法|
|[CA2123](../code-quality/ca2123.md)|重写链接请求应与基相同|
|[CA2124](../code-quality/ca2124.md)|在外部 try 块中包装易受攻击的 finally 子句|
|[CA2126](../code-quality/ca2126.md)|类型链接请求需要继承请求|
|[CA2130](../code-quality/ca2130.md)|安全关键常量应是透明的|
|[CA2131](../code-quality/ca2131.md)|安全关键类型不能参与类型等效|
|[CA2132](../code-quality/ca2132.md)|默认构造函数必须至少与基类型默认构造函数一样关键|
|[CA2133](../code-quality/ca2133.md)|委托必须绑定到具有一致透明度的方法|
|[CA2134](../code-quality/ca2134.md)|在重写基方法时，方法必须保持一致的透明度|
|[CA2135](../code-quality/ca2135.md)|级别 2 程序集不应包含 LinkDemand|
|[CA2136](../code-quality/ca2136.md)|成员不应具有冲突的透明度批注|
|[CA2137](../code-quality/ca2137.md)|透明方法只能包含可验证的 IL|
|[CA2138](../code-quality/ca2138.md)|透明方法不得调用具有 SuppressUnmanagedCodeSecurity 特性的方法|
|[CA2139](../code-quality/ca2139.md)|透明方法不能使用 HandleProcessCorruptingExceptions 特性|
|[CA2140](../code-quality/ca2140.md)|透明代码不得引用安全关键项|
|[CA2141](../code-quality/ca2141.md)|透明方法不得满足 LinkDemand|
|[CA2142](../code-quality/ca2142.md)|不应使用 LinkDemand 保护透明代码|
|[CA2143](../code-quality/ca2143.md)|透明方法不应使用安全请求|
|[CA2144](../code-quality/ca2144.md)|透明代码不应从字节数组加载程序集|
|[CA2145](../code-quality/ca2145.md)|不应使用 SuppressUnmanagedCodeSecurityAttribute 修饰透明方法|
|[CA2146](../code-quality/ca2146.md)|类型必须至少与其基类型和接口一样关键|
|[CA2147](../code-quality/ca2147.md)|透明方法不得使用安全断言|
|[CA2149](../code-quality/ca2149.md)|透明方法不得调入本机代码|
|[CA2210](../code-quality/ca2210.md)|程序集应具有有效的强名称|
|[CA2300](ca2300.md)|请勿使用不安全的反序列化程序 BinaryFormatter|
|[CA2301](ca2301.md)|在未先设置 BinaryFormatter.Binder 的情况下，请不要调用 BinaryFormatter.Deserialize|
|[CA2302](ca2302.md)|在调用 BinaryFormatter.Deserialize 之前，确保设置 BinaryFormatter.Binder|
|[CA2305](ca2305.md)|请勿使用不安全的反序列化程序 LosFormatter|
|[CA2310](ca2310.md)|请勿使用不安全的反序列化程序 NetDataContractSerializer|
|[CA2311](ca2311.md)|在未先设置 NetDataContractSerializer.Binder 的情况下，请不要反序列化|
|[CA2312](ca2312.md)|确保在反序列化之前设置 NetDataContractSerializer.Binder|
|[CA2315](ca2315.md)|请勿使用不安全的反序列化程序 ObjectStateFormatter|
|[CA2321](ca2321.md)|请勿使用 SimpleTypeResolver 对 JavaScriptSerializer 进行反序列化|
|[CA2322](ca2322.md)|确保在反序列化之前没有使用 SimpleTypeResolver 初始化 JavaScriptSerializer|
|[CA3001](../code-quality/ca3001.md)|查看 SQL 注入漏洞的代码|
|[CA3002](../code-quality/ca3002.md)|查看 XSS 漏洞的代码|
|[CA3003](../code-quality/ca3003.md)|查看文件路径注入漏洞的代码|
|[CA3004](../code-quality/ca3004.md)|查看信息泄露漏洞的代码|
|[CA3005](../code-quality/ca3005.md)|查看 LDAP 注入漏洞的代码|
|[CA3006](../code-quality/ca3006.md)|查看进程命令注入漏洞的代码|
|[CA3007](../code-quality/ca3007.md)|查看公开重定向漏洞的代码|
|[CA3008](../code-quality/ca3008.md)|查看 XPath 注入漏洞的代码|
|[CA3009](../code-quality/ca3009.md)|查看 XML 注入漏洞的代码|
|[CA3010](../code-quality/ca3010.md)|查看 XAML 注入漏洞的代码|
|[CA3011](../code-quality/ca3011.md)|查看 DLL 注入漏洞的代码|
|[CA3012](../code-quality/ca3012.md)|查看正则表达式注入漏洞的代码|
|[CA5358](../code-quality/ca5358.md)|不要使用不安全的密码模式|
|[CA5403](../code-quality/ca5403.md)|请勿硬编码证书|
