---
title: 巢狀專案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 35d0f4f8906acc08733894d1c24b6d8c2199e1f7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131156"
---
# <a name="nesting-projects"></a>巢狀專案
企業應用程式開發人員使用您的 VS 套件可以輕鬆地群組類似類型的專案中一起[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用*專案巢狀*。 例如，企業樣板專案會使用巢狀的專案與群組專案組成各種分類。 商務外觀專案、 Web UI 專案等等中群組在一起一個類別目錄。  
  
 在此案例中，開發人員可以巢狀處理每個父專案底下的專案數目沒有限制雖然開發人員可以透過程式設計方式提供限制。 這種類型的群組也可以設定為遞迴、 且在此情況下的子專案與相同類型的專案可以巢狀在要成為子系，也就是父系的子專案的子專案的子系。  
  
 專案的巢狀結構不是內建函式的一部分[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您必須撰寫程式碼來啟用巢狀結構和子專案子專案的巢狀結構。 父專案是特殊的 VSPackage 或專案類型，建立並註冊以包含程式碼，才能實作專案巢狀結構，其專屬 GUID。  
  
 您可以在 C# Example.Nested 專案範例中找到巢狀專案的範例。  
  
## <a name="nested-projects-example"></a>巢狀的專案範例  
 ![巢狀專案方案](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
巢狀的專案範例  
  
## <a name="see-also"></a>另請參閱  
 [如何： 實作巢狀的專案](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [卸載並重新載入巢狀專案的考量](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [巢狀專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [實作處理巢狀專案命令](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [篩選巢狀專案 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [內容參數](../../extensibility/internals/context-parameters.md)   
 [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)