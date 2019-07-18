---
title: HOW TO：偵錯插入程式碼 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35d2343343bf554df7592c8616e7697d88665baf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847790"
---
# <a name="how-to-debug-injected-code"></a>HOW TO：對插入程式碼進行偵錯

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

使用屬性可以大幅簡化 C++ 程式設計。 如需詳細資訊，請參閱 <<c0> [ 概念](/cpp/windows/attributed-programming-concepts)。 有些屬性 (Attribute) 可以直接由編譯器 (Compiler) 解譯。 其他屬性 (Attribute) 會將程式碼插入到編譯器將編譯的程式來源中。 這種插入的程式碼可藉著減少必須由您撰寫的程式碼數量，使程式設計更為容易。 然而，有時一個錯誤便可能會造成應用程式在執行插入程式碼時失敗。 當這種情況發生時，您可能要查看插入程式碼。 Visual Studio 提供兩種讓您查看插入程式碼的方法：

- 您可以在 [反組譯碼] 視窗中檢視插入程式碼。

- 使用 [/Fx](/cpp/build/reference/fx-merge-injected-code)，您可以建立包含原始和插入程式碼的合併來源檔案。

[反組譯碼] 視窗會顯示與原始程式碼和由屬性插入之程式碼對應的組合語言指令。 此外，[反組譯碼] 視窗可以顯示原始程式碼註釋。

## <a name="to-turn-on-source-annotation"></a>若要開啟來源附註

- 以滑鼠右鍵按一下 [反組譯碼] 視窗，並從捷徑功能表選擇 [顯示原始程式碼]。

     如果您知道屬性在來源視窗的位置，您就可以使用捷徑功能表在 [反組譯碼] 視窗裡尋找插入程式碼。

## <a name="to-view-injected-code"></a>若要檢視插入程式碼

1. 偵錯工具必須處於中斷模式。

2. 在原始程式碼視窗裡，將游標放置在您要檢視的插入程式碼的屬性之前。

3. 以滑鼠右鍵按一下，並從捷徑功能表選取 [前往反組譯碼]。

     如果屬性位置距離目前執行點很近，您只要從 [偵錯] 功能表選取 [反組譯碼] 視窗即可。

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>若要檢視目前執行點的反組譯程式碼

1. 偵錯工具必須處於中斷模式。

2. 請在 [偵錯] 功能表中選擇 [視窗]，然後按一下 [反組譯碼]。

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)