---
title: 如何： 檢視指令碼文件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bfa273f98cebdf61f865e03a02c9b2d5f22bfa9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-view-script-documents"></a>如何：檢視指令碼文件
在舊版的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，從伺服器端指令碼產生的用戶端指令碼檔會出現在 [指令碼總管] 視窗中。 [指令碼總管] 視窗通常會隱藏起來，因此用戶端指令碼的存在不一定那麼明顯。  
  
 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，從伺服器端指令碼產生的用戶端指令碼檔會出現在 [指令碼總管] 視窗中，而 [方案總管] 預設為可見狀態。 今後將不再有 [指令碼總管] 視窗。  
  
 只有在您處於偵錯模式或中斷模式時，才會看得見用戶端指令碼檔。 它們會出現在**指令碼文件**節點。  
  
 伺服器端指令碼檔一律可見。 它們會出現在**\<網站路徑名稱 >** 節點。 節點名稱與這個範例類似： `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>若要檢視伺服器端指令碼文件  
  
1.  在**方案總管 中**，開啟**\<網站路徑名稱 >** 節點。  
  
2.  按兩下您想要檢視的指令碼檔。  
  
     伺服器端指令碼檔會在來源視窗中開啟。  
  
### <a name="to-view-a-client-side-script-document"></a>若要檢視用戶端指令碼文件  
  
1.  在**方案總管 中**，開啟**指令碼文件**節點。  
  
2.  按兩下您想要檢視的指令碼檔。  
  
     用戶端指令碼檔會在來源視窗中開啟。  
  
## <a name="see-also"></a>另請參閱  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)