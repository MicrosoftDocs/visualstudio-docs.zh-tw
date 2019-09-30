---
title: Visual Basic 中的 Stop 語句 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f9ab4ef453a921371ab7ef4f272cd0e38f4108a
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322527"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic 中的 Stop 陳述式

Visual Basic 的 Stop 陳述式提供了設定中斷點的程式設計替代方式。 當偵錯工具碰到 Stop 陳述式時，它會中斷程式的執行 (進入中斷模式)。 C#程式設計人員可以使用的呼叫來<xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>達到相同的效果。

您可編輯原始程式碼來設定或移除 Stop 陳述式。 您無法像處理中斷點一樣，使用偵錯工具的命令來設定或清除 Stop 陳述式。

不同於 End 陳述式，Stop 陳述式並不會重設變數，或帶您返回設計模式。 您可選擇 [偵錯] 功能表內的 [繼續] 來繼續執行應用程式。

當您在偵錯工具之外執行 Visual Basic 應用程式時，如果啟用了即時的偵測功能，Stop 語句就會啟動偵錯工具。 如果未啟用即時的偵錯工具，Stop 語句的行為就如同它是 End 語句，而且會終止執行。 不會發生 QueryUnload 或 Unload 事件，因此您必須從 Visual Basic 應用程式的發行版本 (Release Version) 中移除所有的 Stop 陳述式。 如需詳細資訊，請參閱 [Just-In-Time 偵錯](just-in-time-debugging-in-visual-studio.md)。

 若要省略移除 Stop 陳述式的需要，您可使用條件式編譯：

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

另一個替代方式是使用<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>語句，而非 Stop 語句。 只有<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>在不符合指定的條件時，語句才會中斷執行。 <xref:System.Diagnostics.Debug.Assert%2A>當您建立發行版本時，會自動移除語句。 如需詳細資訊，請參閱[受控碼中的判斷提示](assertions-in-managed-code.md)。 如果您想要<xref:System.Diagnostics.Debug.Assert%2A>在 Debug 版本中一律中斷執行的語句，您可以執行下列動作：

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

另一個替代<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>方式是使用方法：

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](debugger-security.md)
- [C#、F# 和 Visual Basic 專案類型](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [偵錯 Managed 程式碼](debugging-managed-code.md)
