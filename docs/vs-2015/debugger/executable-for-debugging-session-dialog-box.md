---
title: 可執行檔進行偵錯工作階段 對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d1279ba5b3ed79c4115143a72e4543bbd6c123d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189822"
---
# <a name="executable-for-debugging-session-dialog-box"></a>偵錯工作階段的可執行檔對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您嘗試對未指定任何可執行檔的 DLL 進行偵錯時，就會出現這個對話方塊。 Visual Studio 無法直接啟動 DLL。 它會改為啟動指定的可執行檔。 您可以對可執行檔呼叫的 DLL 進行偵錯。  
  
 **可執行檔名稱**  
 輸入呼叫您要進行偵錯之 DLL 的可執行檔路徑名稱。  
  
 **專案可以是其中的 URL 存取 (僅限 ATL Server)**  
 如果您要對 ATL 伺服器 DLL 進行偵錯，請輸入可以找到專案的 URL。  
  
 輸入後，這些設定都會儲存在專案的 [屬性頁] 中，如此就不必在後續偵錯工作階段中重新輸入。 如果您需要變更設定，請開啟 [屬性頁] 並變更這些值。 如需有關如何指定偵錯工作階段的可執行檔的詳細資訊，請參閱 <<c0> [ 偵錯 Dll](../debugger/how-to-debug-native-dlls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)



