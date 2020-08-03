---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471569"
---
- 改為使用安全的序列化程式，而**不允許攻擊者指定要還原序列化的任意類型**。 如需詳細資訊，請參閱[慣用的替代方案](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives)。
- 將序列化的資料進行篡改。 序列化之後，以密碼編譯方式簽署序列化的資料。 在還原序列化之前，請驗證密碼編譯簽章。 保護密碼編譯金鑰免于洩漏，並設計金鑰輪替。
- 此選項可讓程式碼容易遭到阻絕服務攻擊，以及未來可能發生的遠端程式碼執行攻擊。 如需詳細資訊，請參閱[BinaryFormatter 安全性指南](/dotnet/standard/serialization/binaryformatter-security-guide)。 限制還原序列化的類型。 執行自訂 <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> 。 在還原序列化之前，請將 `Binder` 屬性設定為您 <xref:System.Runtime.Serialization.SerializationBinder> 在所有程式碼路徑中自訂的實例。 在覆寫的 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> 方法中，如果類型不是預期的，則會擲回例外狀況以停止還原序列化。
