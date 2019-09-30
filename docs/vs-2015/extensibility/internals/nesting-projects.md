---
title: 嵌套專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "68180433"
---
# <a name="nesting-projects"></a>巢狀專案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用您的 VS 套件的企業應用程式開發人員可以使用*專案嵌套*，輕鬆[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]地在中將類似類型的專案群組在一起。 例如，企業範本專案會使用嵌套專案，將專案分組為類別目錄。 商務外觀專案、Web UI 專案等等會在一個類別中群組在一起。  
  
 在此案例中，開發人員可以在每個父專案底下嵌套的專案數沒有任何限制，但開發人員可以透過程式設計方式提供限制。 這種類型的群組也可以設為遞迴，在此情況下，與子專案相同類型的專案可以嵌套在子系底下，成為子系的子專案，也就是父系的子專案。  
  
 專案嵌套不是的內[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]建部分。 您必須撰寫程式碼，才能在子專案中啟用嵌套和子專案的嵌套。 父專案是特殊的 VSPackage 或專案類型，已建立並註冊自己的 GUID，其中包含執行專案嵌套所需的程式碼。  
  
 您可以在C#範例. nested 專案範例中找到嵌套專案的範例。  
  
## <a name="nested-projects-example"></a>嵌套專案範例  
 ![嵌套專案解決方案](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
嵌套專案範例  
  
## <a name="see-also"></a>另請參閱  
 [如何：執行嵌套的專案](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [卸載和重載嵌套專案的考慮](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [支援嵌套專案的 Wizard](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [執行嵌套專案的命令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [篩選嵌套專案的 [AddItem] 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
