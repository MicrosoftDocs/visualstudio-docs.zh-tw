---
title: 如何：重新配置所檢測的二進位檔 | Microsoft Docs
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
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3114ee88feefdbb409ed1a1e1ad025a18123c002
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497974"
---
# <a name="how-to-relocate-instrumented-binaries"></a>如何：重新配置所檢測的二進位檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 重新配置所檢測二進位檔](https://docs.microsoft.com/visualstudio/profiling/how-to-relocate-instrumented-binaries)。  
  
在檢測期間，會將探查插入二進位檔，以便測量應用程式效能。 藉由選擇重新配置所檢測的二進位檔，可以檢測原始二進位檔的複本，並將此複本放在指定的位置。 如果您不想讓分析工具重新命名原始的二進位檔，這個選項會很有用。 如果未重新配置二進位檔，則會覆寫二進位檔的原始版本。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>重新配置所檢測的二進位檔  
  
1.  在 [效能總管] 中，以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性] 。  
  
2.  在 [屬性頁] 中，按一下 [二進位檔]  屬性。  
  
3.  選取 [重新配置所檢測的二進位檔]  核取方塊。  
  
4.  指定所檢測之二進位檔的位置。  
  
## <a name="see-also"></a>另請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)



