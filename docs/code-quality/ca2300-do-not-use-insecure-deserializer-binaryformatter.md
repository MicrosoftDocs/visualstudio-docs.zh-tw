---
title: CA2300：請勿使用不安全的還原序列化程式 BinaryFormatter
ms.date: 04/05/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2300
- DoNotUseInsecureDeserializerBinaryFormatter
ms.openlocfilehash: 13b50e9eba49ff3457aff41d59448f1a0dfc2ea7
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083878"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300：請勿使用不安全的還原序列化程式 BinaryFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

A<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>還原序列化方法已呼叫或參考。

## <a name="rule-description"></a>規則描述

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

此規則會尋找<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>還原序列化方法呼叫或參考。 如果您想要還原序列化時，才<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>屬性設定為 限制類型、 停用此規則及啟用規則[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)並[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)改。

## <a name="how-to-fix-violations"></a>如何修正違規

- 可能的話，請改用安全的序列化程式，並**不會讓攻擊者指定要還原序列化的任意型別**。 某些更安全的序列化程式包括：
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -永不使用<xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>。 如果您必須使用型別解析程式，限制為預期的清單已還原序列化的型別。
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-使用 TypeNameHandling.None。 如果 TypeNameHandling 中，您必須使用另一個值，限制與自訂 ISerializationBinder 預期清單還原序列化的型別。
  - Protocol Buffers
- 使序列化的資料竄改。 在序列化以密碼編譯方式登入序列化的資料。 在還原序列化時之前, 驗證密碼編譯簽章。 保護從被公開的密碼編譯金鑰和金鑰輪替的設計。
- 限制已還原序列化的類型。 實作自訂<xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>。 之前與還原序列化<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>，將<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>執行個體的自訂屬性<xref:System.Runtime.Serialization.SerializationBinder>。 在 覆寫<xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>方法，如果類型是預期的情況，會擲回的例外狀況。
- 如果您限制已還原序列化的型別時，您可能想要停用此規則，然後啟用規則[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)並[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)。 規則[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)並[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)的協助，請確認<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>屬性永遠會設定再還原序列化。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>相關的規則

[CA2301:如果沒有第一個設定 BinaryFormatter.Binder 不呼叫 BinaryFormatter.Deserialize](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302:請確定呼叫 BinaryFormatter.Deserialize 之前設定 BinaryFormatter.Binder](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)