---
title: "CA1024： 在適當時使用屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7a0c0bc8b24ef3ae5fd520a1f277896b533f5194
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024：建議在適當時使用屬性
|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的方法有名稱開頭為`Get`、 不採用任何參數和傳回值，不是陣列。  
  
## <a name="rule-description"></a>規則描述  
 在大部分情況下，內容表示資料，方法會執行動作。 屬性存取欄位，使其更容易使用類似。 方法是成為屬性，如果其中一種情形存在的良好候選項目：  
  
-   不接受引數，並傳回物件的狀態資訊。  
  
-   接受單一引數來設定物件狀態的某些部分。  
  
 屬性應有的行為如同這些欄位。如果方法無法處理，它應該不會變更的屬性。 方法會比在下列情況中的屬性：  
  
-   此方法會執行耗時的作業。 這個方法是設定或取得欄位的值所需的時間比感覺。  
  
-   此方法會執行轉換。 存取欄位不會傳回儲存的資料轉換的版本。  
  
-   Get 方法有副作用。 擷取欄位的值不會產生任何副作用。  
  
-   執行的順序很重要。 設定欄位的值不會依賴其他作業的相符項目。  
  
-   連續兩次呼叫方法會建立不同的結果。  
  
-   方法是靜態的但是會傳回呼叫者可以變更的物件。 擷取欄位的值不允許呼叫端將變更儲存欄位的資料。  
  
-   方法會傳回陣列。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請將方法變更為屬性。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果方法符合至少其中一個先前所列的準則，則隱藏此規則的警告。  
  
## <a name="controlling-property-expansion-in-the-debugger"></a>偵錯工具中控制屬性展開  
 程式設計人員請避免使用屬性的其中一個原因是因為不想要偵錯工具自動展開。 例如，屬性可能牽涉到配置大型物件或呼叫 P/Invoke，但它可能實際上沒有任何副作用。  
  
 您可以避免在偵錯工具自動擴充屬性，藉由套用<xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>。 下列範例會示範這個屬性套用至執行個體屬性。  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```csharp  
  
      using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    publicclass TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## <a name="example"></a>範例  
 下列範例包含數種方法，應該轉換成屬性，以及數個應該就不會報告它們行為不像欄位。  
  
 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]