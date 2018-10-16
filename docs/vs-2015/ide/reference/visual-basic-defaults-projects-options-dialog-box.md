---
title: 選項對話方塊、專案、Visual Basic 預設值 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4c8a1b593333c8b560a828bb0edc5fa7f0628b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274855"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>選項對話方塊、專案、Visual Basic 預設值
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
指定 Visual Basic 專案選項的預設設定。 建立新專案時，會將指定的選項陳述式新增至程式碼編輯器中的專案標頭。 這些選項會套用至所有 Visual Basic 專案。  
  
 若要存取此對話方塊，請在 [工具] 功能表上按一下 [選項]，並展開 [專案和方案] 資料夾，然後按一下 [VB 預設值]。  
  
 **Option Explicit**  
 設定編譯器預設值，因此，需要明確宣告變數。 [Option Explicit] 預設為 [On]。 如需詳細資訊，請參閱 [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7)。  
  
 **Option Strict**  
 設定編譯器預設值；因此，需要明確縮小的轉換，且不允許晚期繫結。 [Option Strict] 預設為 [Off]。 如需詳細資訊，請參閱 [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da)。  
  
 **Option Compare**  
 設定字串比較的編譯器預設值：二進位 (區分大小寫) 或文字 (不區分大小寫)。[Option Compare] 預設為 [Binary]。 如需詳細資訊，請參閱 [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4)。  
  
 **Option Infer**  
 設定區域類型推斷的編譯器預設值。 針對新建立專案，[Option Infer] 預設為 [On]，針對舊版 Visual Basic 中所建立的已移轉專案，則設為 [Off]。 如需詳細資訊，請參閱 [/optioninfer](http://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed)。  
  
## <a name="see-also"></a>另請參閱  
 [專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)



