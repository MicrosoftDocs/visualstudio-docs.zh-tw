---
title: 選項、文字編輯器、F#、程式碼修正
ms.date: 01/16/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.FSharp.Code_Fixes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bbe6b49d7b80138c7fc465e1c86aa13e6bc5e92d
ms.sourcegitcommit: 8bfabab73b39b3b3e68a3e8dc225515e8b310fed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2019
ms.locfileid: "54398368"
---
# <a name="options-text-editor-f-code-fixes"></a>選項、文字編輯器、F#、程式碼修正

使用 [程式碼修正] 選項頁面來指定可協助找出程式碼錯誤並提供解決方案的設定。 若要存取此選項頁面，請選擇 [工具] > [選項]，然後選擇 [文字編輯器] > [F#] > [程式碼修正]。

## <a name="code-fixes"></a>程式碼修正

- **簡化名稱 (移除不必要的限定詞)**

   如果選取此核取方塊，則在不需要限定詞時會簡化完整名稱，例如經常使用的命名空間的成員。

- **一律將 open 陳述式放在最上層**

   如果選取此核取方塊並在程式碼中輸入 open 陳述式，則將其置於最上層。

- **移除未使用的 open 陳述式**

   如果選取此核取方塊，則會刪除目前檔案中未使用的 open 陳述式。

- **分析並建議修正未使用的值**

   如果選取此核取方塊，則工具會辨識程式碼中未使用的值。 然後，如果將滑鼠暫留在未使用的值上，它會建議您使用該值的方法。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
- [尋找 CodeLens 的程式碼變更和其他記錄](../../ide/find-code-changes-and-other-history-with-codelens.md)