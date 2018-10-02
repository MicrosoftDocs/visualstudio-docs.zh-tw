---
title: 如何： 檢視指令碼文件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc24c5e9c2332516cbf939e14581a2df7bea44eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496570"
---
# <a name="how-to-view-script-documents"></a>如何：檢視指令碼文件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[How to: View Script Documents](https://docs.microsoft.com/visualstudio/debugger/how-to-view-script-documents)。  
  
在舊版的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中，從伺服器端指令碼產生的用戶端指令碼檔會出現在 [指令碼總管] 視窗中。 [指令碼總管] 視窗通常會隱藏起來，因此用戶端指令碼的存在不一定那麼明顯。  
  
 在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中，從伺服器端指令碼產生的用戶端指令碼檔會出現在 [指令碼總管] 視窗中，而 [方案總管] 預設為可見狀態。 今後將不再有 [指令碼總管] 視窗。  
  
 只有在您處於偵錯模式或中斷模式時，才會看得見用戶端指令碼檔。 它們會出現在**指令碼文件**節點。  
  
 伺服器端指令碼檔一律可見。 它們會出現在**\<網站路徑名稱 >** 節點。 節點的名稱會類似以下範例： `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>若要檢視伺服器端指令碼文件  
  
1.  在 **方案總管**，開啟**\<網站路徑名稱 >** 節點。  
  
2.  按兩下您想要檢視的指令碼檔。  
  
     伺服器端指令碼檔會在來源視窗中開啟。  
  
### <a name="to-view-a-client-side-script-document"></a>若要檢視用戶端指令碼文件  
  
1.  在 **方案總管**，開啟**指令碼文件**節點。  
  
2.  按兩下您想要檢視的指令碼檔。  
  
     用戶端指令碼檔會在來源視窗中開啟。  
  
## <a name="see-also"></a>另請參閱  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)



