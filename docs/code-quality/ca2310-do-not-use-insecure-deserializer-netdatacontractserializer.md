---
title: CA2310:請勿使用不安全的還原序列化程式 NetDataContractSerializer
ms.date: 05/01/2019
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
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: e4af6bbfbd7e14b99f39ffa0adb5d1117c200d9a
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135426"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310:請勿使用不安全的還原序列化程式 NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

A<xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType>還原序列化方法已呼叫或參考。

## <a name="rule-description"></a>規則描述

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

此規則會尋找<xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType>還原序列化方法呼叫或參考。 如果您想要還原序列化時，才<xref:System.Runtime.Serialization.NetDataContractSerializer.Binder>屬性設定為 限制類型、 停用此規則及啟用規則[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)並[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)改。

## <a name="how-to-fix-violations"></a>如何修正違規

- 可能的話，請改用安全的序列化程式，並**不會讓攻擊者指定要還原序列化的任意型別**。 某些更安全的序列化程式包括：
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -永不使用<xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>。 如果您必須使用型別解析程式，限制為預期的清單已還原序列化的型別。
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-使用 TypeNameHandling.None。 如果 TypeNameHandling 中，您必須使用另一個值，限制與自訂 ISerializationBinder 預期清單還原序列化的型別。
  - Protocol Buffers
- 使序列化的資料竄改。 在序列化以密碼編譯方式登入序列化的資料。 在還原序列化時之前, 驗證密碼編譯簽章。 保護從被公開的密碼編譯金鑰和金鑰輪替的設計。
- 限制已還原序列化的類型。 實作自訂<xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>。 之前與還原序列化<xref:System.Runtime.Serialization.NetDataContractSerializer>，將<xref:System.Runtime.Serialization.NetDataContractSerializer.Binder>執行個體的自訂屬性<xref:System.Runtime.Serialization.SerializationBinder>。 在 覆寫<xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>方法，如果類型是預期的情況，會擲回的例外狀況。
- 如果您限制已還原序列化的型別時，您可能想要停用此規則，然後啟用規則[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)並[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)。 規則[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)並[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)的協助，請確認<xref:System.Runtime.Serialization.NetDataContractSerializer.Binder>屬性永遠會設定再還原序列化。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>相關的規則

[CA2311:無法還原序列化而不需要第一個設定 NetDataContractSerializer.Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312:請確定 NetDataContractSerializer.Binder 設定後再進行還原序列化](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
