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
ms.openlocfilehash: c833a60d98cbfd7eea3e3b673c7e60c6047a4ae9
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083899"
---
# <a name="ca2302-ensure-binaryformatterbinder-is-set-before-calling-binaryformatterdeserialize"></a>CA2302：呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder

|||
|-|-|
|TypeName|EnsureBinaryFormatterBinderIsSetBeforeCallingBinaryFormatterDeserialize|
|CheckId|CA2302|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

A<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>還原序列化方法已呼叫或參考和<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>屬性可能是 null。

## <a name="rule-description"></a>規則描述

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

此規則會尋找<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>還原序列化方法呼叫或參考時<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>可能為 null。 如果您想要禁止使用的任何還原序列化<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>不論<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>屬性，停用此規則並[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)，並啟用規則[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)。

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
  - 請確定所有的程式碼路徑有<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder>屬性集。

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

## <a name="related-rules"></a>相關的規則

[CA2300:請勿使用不安全還原 BinaryFormatter 序列化程式](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2301:如果沒有第一個設定 BinaryFormatter.Binder 不呼叫 BinaryFormatter.Deserialize](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)
