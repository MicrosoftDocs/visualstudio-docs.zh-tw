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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180433"
---
# <a name="nesting-projects"></a>巢狀專案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用您的 VS 封裝的企業應用程式開發人員可以 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 使用 *專案嵌套*，輕鬆地在中將類似的專案群組在一起。 例如，企業範本專案會使用嵌套專案將專案分組為類別。 商務外觀專案、Web UI 專案等會在一個類別中群組在一起。  
  
 在此案例中，開發人員可以在每個父專案下嵌套的專案數目沒有任何限制，但開發人員可以用程式設計的方式提供限制。 這種類型的群組也可以遞迴進行，在這種情況下，與子專案相同類型的專案可以嵌套在子專案下，成為子專案的子專案，也就是父系的子專案。  
  
 專案嵌套不是的內建部分 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 您必須撰寫程式碼，才能在子專案內啟用嵌套和子專案的嵌套。 父專案是特殊的 VSPackage 或專案類型，使用自己的 GUID 建立和註冊，其中包含執行專案嵌套所需的程式碼。  
  
 您可以在 c # 範例中找到嵌套專案範例。嵌套專案範例。  
  
## <a name="nested-projects-example"></a>嵌套專案範例  
 ![巢狀專案方案](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
嵌套專案範例  
  
## <a name="see-also"></a>另請參閱  
 [如何：執行嵌套專案](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [卸載和重載嵌套專案的考慮](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [針對嵌套專案的 Wizard 支援](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [執行嵌套專案的命令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [篩選嵌套專案的 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
