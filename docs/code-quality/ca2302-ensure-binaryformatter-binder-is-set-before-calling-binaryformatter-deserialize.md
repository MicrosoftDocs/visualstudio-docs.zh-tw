---
title: CA2302：呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder
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
- CA2302
- EnsureBinaryFormatterBinderIsSetBeforeCallingBinaryFormatterDeserialize
ms.openlocfilehash: 90e17211bc30dc65ce78b738dc692d5dbb7aaa69
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237736"
---
# <a name="ca2302-ensure-binaryformatterbinder-is-set-before-calling-binaryformatterdeserialize"></a>CA2302：呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder

|||
|-|-|
|TypeName|EnsureBinaryFormatterBinderIsSetBeforeCallingBinaryFormatterDeserialize|
|CheckId|CA2302|
|分類|Microsoft.Security|
|重大變更|不中斷|

## <a name="cause"></a>原因

已呼叫或參考還原序列化方法<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> ，而且屬性可能是 null。 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>

## <a name="rule-description"></a>規則描述

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

當可能是<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> null 時， <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>此規則會尋找還原序列化方法呼叫或參考。 如果您想<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>要不使用任何<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>屬性來禁止任何還原序列化，請停用此規則並[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)，然後啟用規則[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)。

## <a name="how-to-fix-violations"></a>如何修正違規

- 可能的話，請改為使用安全的序列化程式，而**不允許攻擊者指定要還原序列化的任意類型**。 一些較安全的序列化套裝程式括：
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-永不使用<xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>。 如果您必須使用類型解析程式，請將還原序列化的類型限制為預期的清單。
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-使用 TypeNameHandling。 如果您必須使用另一個值來進行 TypeNameHandling，請將已還原序列化的類型限制為具有自訂 ISerializationBinder 的預期清單。
  - 通訊協定緩衝區
- 將序列化的資料進行篡改。 序列化之後，以密碼編譯方式簽署序列化的資料。 在還原序列化之前，請驗證密碼編譯簽章。 保護密碼編譯金鑰免于洩漏，並設計金鑰輪替。
- 限制還原序列化的類型。 執行自訂<xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>。 在還原序列化<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>之前，請<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>將屬性設定為自訂<xref:System.Runtime.Serialization.SerializationBinder>的實例。 在覆寫<xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>的方法中，如果類型不是預期的，則會擲回例外狀況以停止還原序列化。
  - 請確定所有程式碼路徑都<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>已設定屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BinaryFormatter Formatter { get; set; }

    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) this.Formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Property Formatter As BinaryFormatter

    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(Me.Formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>方案

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Binary;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", nameof(typeName));
        }
    }
}

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        formatter.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization
Imports System.Runtime.Serialization.Formatters.Binary

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", NameOf(typeName))
        End If
    End Function
End Class

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        formatter.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>相關規則

[CA2300:請勿使用不安全的還原序列化 BinaryFormatter](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2301:請勿呼叫 BinaryFormatter，而不先設定 BinaryFormatter。](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)
