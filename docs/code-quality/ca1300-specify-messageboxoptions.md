---
title: CA1300:必須指定 MessageBoxOptions
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bd269b099095326a260da7613bf3c2c402e864be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797695"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300:必須指定 MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|分類|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因

方法會呼叫的多載<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>方法不接受<xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>引數。

## <a name="rule-description"></a>規則描述

若要顯示訊息方塊中，針對使用由右至左讀取順序的文化特性的正確，請傳遞[MessageBoxOptions.RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>)並[MessageBoxOptions.RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>)欄位<xref:System.Windows.Forms.MessageBox.Show%2A>方法。 檢查<xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>來判斷是否要使用由右至左讀取順序，包含控制項的屬性。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，呼叫的多載<xref:System.Windows.Forms.MessageBox.Show%2A>採用方法<xref:System.Windows.Forms.MessageBoxOptions>引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它會安全地隱藏此規則的警告時不會使用由右至左讀取順序的文化特性當地語系化程式碼程式庫。

## <a name="example"></a>範例

下列範例會顯示訊息方塊具有適當的文化特性的讀取順序選項的方法。 資源檔，不會顯示，它才能建置範例。 請依照下列範例中，若要建置沒有資源檔範例，並測試從右至左功能中的註解。

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [桌面應用程式中的資源 (.NET Framework)](/dotnet/framework/resources/index)