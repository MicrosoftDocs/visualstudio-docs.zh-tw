---
title: 選項對話方塊、專案、Visual Basic 預設值 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f08cc817fab6e81ae1160462c9b6d1221ca41160
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657879"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>選項對話方塊、專案、Visual Basic 預設值
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定 Visual Basic 專案選項的預設設定。 建立新專案時，會將指定的選項陳述式新增至程式碼編輯器中的專案標頭。 這些選項會套用至所有 Visual Basic 專案。

 若要存取此對話方塊，請在 [工具]  功能表上按一下 [選項]  ，並展開 [專案和方案]  資料夾，然後按一下 [VB 預設值]  。

 **Option Explicit**設定編譯器預設值，讓變數的明確宣告為必要項。 [Option Explicit]  預設為 [On]  。 如需詳細資訊，請參閱 [/optionexplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7)。

 **Option Strict**設定編譯器預設值，以便需要明確的縮小轉換，而且不允許晚期繫結。 [Option Strict]  預設為 [Off]  。 如需詳細資訊，請參閱 [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da)。

 **選項比較**設定字串比較的編譯器預設值：二進位（區分大小寫）或文字（不區分大小寫）。[Option Compare] 預設為 [Binary]  。 如需詳細資訊，請參閱 [/optioncompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4)。

 **選項推斷**設定區欄位型別推斷的編譯器預設值。 針對新建立專案，[Option Infer]  預設為 [On]  ，針對舊版 Visual Basic 中所建立的已移轉專案，則設為 [Off]  。 如需詳細資訊，請參閱 [/optioninfer](https://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed)。

## <a name="see-also"></a>另請參閱
 [專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)
