---
title: 如何：指定其他的檢測選項 | Microsoft Docs
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
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1726a8ad414ca6450f056044d520f73021c59f46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490645"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>如何：指定其他的檢測選項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 指定其他的檢測選項](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-additional-instrumentation-options)。  
  
您可以從 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 整合式開發環境 (IDE) 中或是使用命令列工具檢測二進位檔。 如果是從 IDE 中檢測二進位檔，您可以為 [VSInstr](../profiling/vsinstr.md) 工具指定其他的檢測選項，藉以控制檢測期間所收集的資料量。 這些選項可以在工作階段或目標層級中使用。 例如，若要在檢測程序期間包含或排除特定函式，請在目標層級使用其他的檢測選項。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
>  插入的每個探查會稍微改變原始程式的行為。 這個改變會在分析階段造成額外負荷。 即使扣除掉這個額外負荷的近似值，它仍會對多執行緒的應用程式有輕微的執行時間變化。 [VSInstr](../profiling/vsinstr.md) 工具選項可協助在程式碼剖析期間控制資料的收集。  
  
### <a name="to-specify-additional-instrumentation-option"></a>指定其他的檢測選項  
  
1.  在 [效能總管] 中，選取 [效能工作階段]，然後以滑鼠右鍵按一下並選取 [屬性]。  
  
2.  在 [屬性頁] 中，按一下 [進階] 屬性。  
  
3.  在 [其他檢測選項] 方塊中輸入選項。  
  
     例如，使用 /CONTROL:THREAD 以指定程式碼剖析層級。 如需選項的完整清單，請參閱 [VSInstr](../profiling/vsinstr.md)。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="see-also"></a>另請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)



