---
title: FxCopCmd 錯誤
ms.date: 10/19/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.author: jillfra
author: jillre
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85441e90bfecc89688ce0ba6ec0ae10082562f0e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667589"
---
# <a name="fxcopcmd-tool-errors"></a>Fxcopcmd.exe 工具錯誤

Fxcopcmd.exe 不會將所有錯誤視為嚴重。 如果 Fxcopcmd.exe 有足夠的資訊可執行部分分析，它會執行分析並報告發生的錯誤。 錯誤碼是32位整數，其中包含對應至錯誤之數值的位元組合。

下表說明 Fxcopcmd.exe 所傳回的錯誤碼：

|錯誤|數值|
|-----------|-------------------|
|沒有錯誤|0x0|
|分析錯誤|0x1|
|規則例外狀況|0x2|
|專案載入錯誤|0x4|
|元件載入錯誤|0x8|
|規則程式庫載入錯誤|0x10|
|匯入報告載入錯誤|0x20|
|輸出錯誤|0x40|
|命令列參數錯誤|0x80|
|初始化錯誤|0x100|
|元件參考錯誤|0x200|
|BuildBreakingMessage|0x400|
|未知的錯誤|0x1000000|

發生嚴重錯誤時，會傳回**分析錯誤**。 這表示無法完成分析。 當適用時，錯誤碼也會包含嚴重錯誤的根本原因。 下列條件會產生嚴重錯誤：

- 因為輸入不足，所以無法執行分析。

- 分析擲回不是由 Fxcopcmd.exe 處理的例外狀況。

- 找不到指定的專案檔案或其已損毀。

- 未指定輸出選項，或無法寫入檔案。

> [!NOTE]
> Fxcopcmd.exe 傳回程序代碼**元件本身會參考錯誤**0x200，而不是錯誤。 此傳回碼表示缺少間接參考，但該 Fxcopcmd.exe 能夠處理它們。 此警告表示某些分析結果可能已遭入侵。 將**元件參考錯誤**與任何其他傳回碼結合時，視為錯誤。

## <a name="see-also"></a>請參閱

- [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)