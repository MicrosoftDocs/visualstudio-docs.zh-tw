---
title: 選項、文字編輯器、F#、程式碼修正
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5c736be59c257d98085831971d6b7b9dc2a0ef3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "72666274"
---
# <a name="options-text-editor--f--code-fixes"></a>選項：文字編輯器> F# >代碼修復

使用 [程式碼修正] 選項頁面來指定可協助找出程式碼錯誤並提供解決方案的設定。 要訪問此選項頁，請選擇 **"工具** > **選項**"，然後選擇**文字編輯器** > **F#** > **代碼修復**。

## <a name="code-fixes"></a>程式碼修正

- **簡化名稱 (移除不必要的限定詞)**

  如果選取此核取方塊，則在不需要限定詞時會簡化完整名稱，例如經常使用的命名空間的成員。

- **一律將 open 陳述式放在最上層**

  如果選取此核取方塊並在程式碼中輸入 `open` 陳述式，則會將其置於最上層。

- **移除未使用的 open 陳述式**

  如果選取此核取方塊，則會針對未使用的 `open` 陳述式分析文件，且會顯示[快速控制項目](../quick-actions.md)燈泡，其具有移除所有未使用 `open` 陳述式的動作。

- **分析並建議修正未使用的值**

  如果選取此核取方塊，則工具會辨識程式碼中未使用的值。 然後，如果將滑鼠暫留在未使用的值上，它會建議您使用該值的方法。

## <a name="see-also"></a>另請參閱

- [常規、環境、選項對話方塊](../../ide/reference/general-environment-options-dialog-box.md)
- [尋找 CodeLens 的程式碼變更和其他記錄](../../ide/find-code-changes-and-other-history-with-codelens.md)
