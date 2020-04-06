---
title: 選擇除錯引擎實施策略 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739123"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>選擇除錯引擎實施原則
使用運行時體系結構確定調試引擎 (DE) 實現策略。 您可以將除錯引擎建立到正在除錯的程式的程序。 在過程中創建調試引擎到可視化工作室工作階段除錯管理器 (SDM)。 或者,將調試引擎創建進程外,以將其與它們進行。 以下指南將説明您從這三種策略中進行選擇。

## <a name="guidelines"></a>指導方針
 雖然 DE 可能會與 SDM 和正在調試的程式都進行進程外處理,但通常沒有理由這樣做。 跨進程邊界的調用相對較慢。

 已經為 Win32 本機運行時環境和通用語言運行時環境提供了調試引擎。 如果必須為任一環境替換 DE,則應使用 SDM 創建進程中的 DE。

 否則,您將在進程中創建 DE 到 SDM 或行程內到要調試的程式。 您需要考慮 DE 的運算式賦值器是否需要頻繁存取程式符號儲存。 或者,如果符號存儲可以載入到記憶體中以便快速存取。 此外,請考慮以下方法:

- 如果表達式賦值器和符號存儲之間沒有多次調用,或者如果符號存儲可以讀取到 SDM 記憶體空間中,請創建 SDM 過程中的 DE 進程。 當除錯引擎的 CLSID 附加到程式時,必須將其返回到 SDM。 SDM 使用此 CLSID 創建 DE 的程序內實例。

- 如果 DE 必須呼叫程式才能存取符號儲存,請使用程式創建進程中的 DE。 在這種情況下,程式將創建 DE 的實例。

## <a name="see-also"></a>另請參閱
- [視覺化工作室除錯器可擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
