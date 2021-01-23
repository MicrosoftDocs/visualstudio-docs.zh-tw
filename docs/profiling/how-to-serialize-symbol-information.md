---
title: 將符號資訊序列化 | Microsoft Docs
description: 瞭解如何序列化必須用來分析應用程式的符號，以及符號序列化如何將符號加入 .vsp 檔案。
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b7cdfa6e64380c966b62d6691f73719a3034e2d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722083"
---
# <a name="how-to-serialize-symbol-information"></a>如何：序列化符號資訊
您可以將分析應用程式所需的符號序列化。 符號序列化會將符號新增至 .*vsp* 檔案。 透過將符號資訊新增至 .*vsp* 檔案，其他人就算沒有原始符號的存取權也可以分析效能報告。 如果符號未序列化，您必須擁有原始的已檢測 .*exe* 和 .*pdb* 檔案才能分析 .*vsp* 檔案。

### <a name="to-automatically-serialize-symbol-information"></a>自動序列化符號資訊

1. 在 **[工具]** 功能表上，按一下 **[選項]** 。

     [選項] 對話方塊即會出現。

2. 按一下 [效能工具]。

3. 在 [一般設定] 下方，選取 [自動序列化符號資訊]。

## <a name="see-also"></a>另請參閱
- [設定效能工作階段](../profiling/configuring-performance-sessions.md)
- [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)
- [如何：儲存分析的報告檔案](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
