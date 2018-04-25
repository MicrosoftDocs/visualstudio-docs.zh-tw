---
title: 選項對話方塊、專案、Visual Basic 預設值 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 727342a48e19d6094fa235c09c6e9d3bed163311
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>選項對話方塊、專案、Visual Basic 預設值
指定 Visual Basic 專案選項的預設設定。 建立新專案時，會將指定的選項陳述式新增至程式碼編輯器中的專案標頭。 這些選項會套用至所有 Visual Basic 專案。  
  
 若要存取此對話方塊，請在 [工具] 功能表上按一下 [選項]，並展開 [專案和方案] 資料夾，然後按一下 [VB 預設值]。  
  
 **Option Explicit**  
 設定編譯器預設值，因此，需要明確宣告變數。 [Option Explicit] 預設為 [On]。 如需詳細資訊，請參閱 [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)。  
  
 **Option Strict**  
 設定編譯器預設值；因此，需要明確縮小的轉換，且不允許晚期繫結。 [Option Strict] 預設為 [Off]。 如需詳細資訊，請參閱 [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)。  
  
 **Option Compare**  
 設定字串比較的編譯器預設值：二進位 (區分大小寫) 或文字 (不區分大小寫)。[Option Compare] 預設為 [Binary]。 如需詳細資訊，請參閱 [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)。  
  
 **Option Infer**  
 設定區域類型推斷的編譯器預設值。 針對新建立專案，[Option Infer] 預設為 [On]，針對舊版 Visual Basic 中所建立的已移轉專案，則設為 [Off]。 如需詳細資訊，請參閱 [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)。  
  
## <a name="see-also"></a>請參閱  
 [專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)