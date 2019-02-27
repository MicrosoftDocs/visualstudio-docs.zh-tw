---
title: HOW TO：將符號資訊序列化 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72a634bd83a55d4e646874cce5546e2a7310afb2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617843"
---
# <a name="how-to-serialize-symbol-information"></a>作法：序列化符號資訊
您可以將分析應用程式所需的符號序列化。 符號序列化會將符號新增至 .*vsp* 檔案。 透過將符號資訊新增至 .*vsp* 檔案，其他人就算沒有原始符號的存取權也可以分析效能報告。 如果符號未序列化，您必須擁有原始的已檢測 .*exe* 和 .*pdb* 檔案才能分析 .*vsp* 檔案。

### <a name="to-automatically-serialize-symbol-information"></a>自動序列化符號資訊

1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。

     [選項] 對話方塊即會出現。

2.  按一下 [效能工具]。

3.  在 [一般設定] 下方，選取 [自動序列化符號資訊]。

## <a name="see-also"></a>另請參閱
- [設定效能工作階段](../profiling/configuring-performance-sessions.md)
- [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)
- [如何：儲存分析的報告檔案](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))