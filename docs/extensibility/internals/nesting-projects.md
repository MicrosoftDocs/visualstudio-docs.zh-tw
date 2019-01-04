---
title: 巢狀專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38b0544d58362a37113b0e193324a2ef5b8cdb49
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860984"
---
# <a name="nesting-projects"></a>巢狀專案
企業應用程式開發人員使用您的 VS 套件可以方便地分組類似類型的專案在一起[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]利用*專案的巢狀結構*。 例如，Enterprise 範本專案會使用巢狀的群組專案的專案成類別目錄。 商業外觀專案、 Web UI 專案等等，則會在一個類別一起分組。  
  
 在此案例中，沒有任何限制的開發人員可以巢狀處理每個父專案底下的專案數目雖然開發人員可以透過程式設計方式提供限制。 這種類型的群組也可以設定為遞迴的在此情況下相同的型別，做為子專案的專案可以巢狀在要成為子系，也就是父系的子專案的子專案的子系。  
  
 專案的巢狀結構不是內建函式的一部分[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您必須撰寫程式碼來啟用巢狀結構，以及子子專案的巢狀結構。 父專案是特殊的 VSPackage 或專案類型，建立並登錄與包含的程式碼，才能實作專案巢狀結構，其專屬 GUID。  
  
 您可以在 C# Example.Nested 專案範例中找到巢狀專案的範例。  
  
## <a name="nested-projects-example"></a>巢狀的專案範例  
 ![巢狀專案方案](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
巢狀的專案範例  
  
## <a name="see-also"></a>另請參閱  
 [如何：實作巢狀的專案](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [卸載並重新載入巢狀專案的考量](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [巢狀專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [實作處理巢狀專案的命令](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [篩選巢狀專案的 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)