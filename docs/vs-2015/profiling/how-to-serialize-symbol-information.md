---
title: 如何：序列化符號資訊 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04bce9383142ee6916fa7ade50feda072019f530
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496547"
---
# <a name="how-to-serialize-symbol-information"></a>如何：序列化符號資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 序列化符號資訊](https://docs.microsoft.com/visualstudio/profiling/how-to-serialize-symbol-information)。  
  
您可以將分析應用程式所需的符號序列化。 符號序列化會將符號加入至 .vsp 檔案。 透過將符號資訊加入至 .vsp 檔案，其他人就算沒有原始符號的存取權也可以分析效能報告。 如果符號未序列化，您必須擁有原始的已檢測 .exe 和 .pdb 檔案才能分析 .vsp 檔案。  
  
### <a name="to-automatically-serialize-symbol-information"></a>自動序列化符號資訊  
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
     [選項] 對話方塊即會出現。  
  
2.  按一下 [效能工具]。  
  
3.  在 [一般設定] 下方，選取 [自動序列化符號資訊]。  
  
## <a name="see-also"></a>另請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)   
 [如何：儲存分析的報告檔案](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)



