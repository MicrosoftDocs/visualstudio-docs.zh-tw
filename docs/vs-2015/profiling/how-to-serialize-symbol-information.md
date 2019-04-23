---
title: HOW TO：將符號資訊序列化 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b29ddb0e88a58fbfd924c40134305cf33a3e170b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103793"
---
# <a name="how-to-serialize-symbol-information"></a>HOW TO：序列化符號資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將分析應用程式所需的符號序列化。 符號序列化會將符號加入至 .vsp 檔案。 透過將符號資訊加入至 .vsp 檔案，其他人就算沒有原始符號的存取權也可以分析效能報告。 如果符號未序列化，您必須擁有原始的已檢測 .exe 和 .pdb 檔案才能分析 .vsp 檔案。  
  
### <a name="to-automatically-serialize-symbol-information"></a>自動序列化符號資訊  
  
1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
     [選項] 對話方塊即會出現。  
  
2. 按一下 [效能工具]。  
  
3. 在 [一般設定] 下方，選取 [自動序列化符號資訊]。  
  
## <a name="see-also"></a>另請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)   
 [如何：儲存分析的報告檔案](http://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
