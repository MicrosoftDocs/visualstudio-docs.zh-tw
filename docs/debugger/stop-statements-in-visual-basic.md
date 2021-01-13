---
title: Visual Basic 中的 Stop 語句 |Microsoft Docs
description: 請參閱 Visual Basic Stop 語句，這會提供在 Visual Studio 中設定中斷點的程式設計替代方式。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b36f00f628d9551d8e45075d790d8e5d2de294dc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149426"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic 中的 Stop 陳述式

Visual Basic 的 Stop 陳述式提供了設定中斷點的程式設計替代方式。 當偵錯工具碰到 Stop 陳述式時，它會中斷程式的執行 (進入中斷模式)。 C # 程式設計人員可以使用的呼叫來達成相同的效果 <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> 。

您可編輯原始程式碼來設定或移除 Stop 陳述式。 您無法像處理中斷點一樣，使用偵錯工具的命令來設定或清除 Stop 陳述式。

不同於 End 陳述式，Stop 陳述式並不會重設變數，或帶您返回設計模式。 您可選擇 [偵錯] 功能表內的 [繼續] 來繼續執行應用程式。

當您在偵錯工具外部執行 Visual Basic 應用程式時，如果啟用了即時偵錯工具，Stop 語句會啟動偵錯工具。 如果未啟用即時偵錯工具，Stop 語句的行為就像是 End 語句並結束執行。 不會發生 QueryUnload 或 Unload 事件，因此您必須從 Visual Basic 應用程式的發行版本 (Release Version) 中移除所有的 Stop 陳述式。 如需詳細資訊，請參閱 [Just-In-Time 偵錯](just-in-time-debugging-in-visual-studio.md)。

 若要省略移除 Stop 陳述式的需要，您可使用條件式編譯：

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

另一個替代方法是使用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 語句，而非 Stop 語句。 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>只有在不符合指定的條件時，語句才會中斷執行。 <xref:System.Diagnostics.Debug.Assert%2A> 當您建立發行版本時，會自動移除語句。 如需詳細資訊，請參閱[受控碼中的判斷提示](assertions-in-managed-code.md)。 如果您想要在 <xref:System.Diagnostics.Debug.Assert%2A> Debug 版本中一律中斷執行的語句，您可以執行下列動作：

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

還有另一個替代方法是使用 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> 方法：

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
