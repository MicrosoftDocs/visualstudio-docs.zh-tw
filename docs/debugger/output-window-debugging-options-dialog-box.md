---
title: 選項對話方塊、輸出視窗、調試Microsoft Docs
description: 您可以指定要在 [輸出] 視窗中顯示哪些類型的偵錯資訊。 瞭解如何進行這項作業，以及您可以控制的資訊類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.OutputWindow
- VS.ToolsOptionsPages.Debugger.OutputWindow
- vs.debug.options.Output
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: d67387c2-39e9-4790-93bc-e41bff12fb9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7f74b0e490cf8b2baaa8818fa8f8eebb7842a30
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975013"
---
# <a name="output-window-debugging-options-dialog-box"></a>選項對話方塊、偵錯、輸出視窗
您可以指定要在 [輸出] 視窗中顯示哪些類型的偵錯資訊。 若要顯示這些選項，請開啟 [工具] 功能表、按一下 [選項]、展開 [偵錯] 節點，然後按一下 [輸出] 視窗。

**一般輸出設定** 這個類別包含的控制項可決定一般的 debug 訊息是否出現在 [ **輸出** ] 視窗中。 您可以指定是否顯示每一種訊息類型。

**WPF 追蹤設定** 這個類別包含的控制項可決定出現在 [ **輸出** ] 視窗中的 WPF 追蹤訊息層級。 您可以指定是否顯示每種類型的訊息，並指定範圍從 **「關鍵」** 到 **「所有」** 的層級。

如需詳細資訊，請參閱 [如何：顯示 WPF 追蹤資訊](../debugger/how-to-display-wpf-trace-information.md)。

如果您需要還原預設設定，可以使用 [**工具** 匯  >  **入和匯出設定**]  >  **重設所有設定**。 如果您只想要重設設定子集，請先在 [匯 **入和匯出設定] 嚮導** 中儲存設定，然後再進行要測試的變更，然後稍後再匯入儲存的設定。

## <a name="see-also"></a>請參閱
- [選項對話方塊、調試](../debugger/debugging-options-dialog-box.md)
- [輸出視窗](../ide/reference/output-window.md)