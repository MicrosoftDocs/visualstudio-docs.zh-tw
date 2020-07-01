---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: bc423f10cfbae0b7a0cdaedb72f6891a0e12d228
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147117"
---
- 可能的話，請改為使用安全的序列化程式，而**不允許攻擊者指定要還原序列化的任意類型**。 一些較安全的序列化套裝程式括：
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-永不使用 <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> 。 如果您必須使用類型解析程式，請將還原序列化的類型限制為預期的清單。
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-使用 TypeNameHandling。 如果您必須使用另一個值來進行 TypeNameHandling，請將已還原序列化的類型限制為具有自訂 ISerializationBinder 的預期清單。
  - 通訊協定緩衝區
- 將序列化的資料進行篡改。 序列化之後，以密碼編譯方式簽署序列化的資料。 在還原序列化之前，請驗證密碼編譯簽章。 保護密碼編譯金鑰免于洩漏，並設計金鑰輪替。