---
title: "使用 Project Factory 建立的專案執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7175bd4e2d0b07640dd45b38aa246c649def32ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-project-instances-by-using-project-factories"></a>使用 Project Factory 建立的專案執行個體
專案中的型別[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用*專案 factory*建立專案中物件的執行個體。 專案 factory 是類似於標準的 class factory cocreatable COM 物件。 不過，專案物件不是 cocreatable： 只可以建立使用專案 factory。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 呼叫 project factory 使用者載入現有的專案，或建立新的專案中時，在 VSPackage 中實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 新的專案物件會提供 IDE，具有足夠的資訊填入 [方案總管] 中。 新的專案物件也會提供所需的介面以支援由 IDE 所起始的所有相關 UI 動作。  
  
 您可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>中您的專案中的類別介面。 通常，它位於自己的模組。  
  
 如需範例實作的`IVsProjectFactory`介面，請參閱中所包含的 PrjFac.cpp[基本專案](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36)範例目錄。  
  
 支援彙總的擁有者專案必須保存其專案檔中的擁有者金鑰。 當<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>與擁有者索引鍵呼叫方法在專案上，擁有的專案將其擁有者索引鍵轉換成 GUID 然後呼叫專案 factory`CreateProject`上進行實際建立這個專案 factory 方法。  
  
## <a name="creating-an-owned-project"></a>建立擁有的專案  
 擁有者會建立兩個階段中擁有的專案：  
  
1.  藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>方法。 這可讓擁有的專案建立根據輸入控制彙總的專案物件有機會`IUnknown`。 擁有的專案會傳遞內部`IUnknown`和彙總的物件傳回至擁有者專案。 這可讓擁有的專案有機會儲存內部`IUnknown`。  
  
2.  藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>方法。 擁有的專案沒有所有其具現化，而不是呼叫呼叫這個方法`IVsProjectFactory::CreateProject`如下的情況不屬於的專案。 輸入`VSOWNEDPROJECTOBJECT`列舉型別通常是彙總的擁有的專案。 擁有的專案可以使用這個變數來判斷是否已建立其專案物件 （cookie 不等於 NULL） 或必須在建立 （cookie 等於 NULL）。  
  
 唯一的專案 GUID，類似於 cocreatable 的 COM 物件的 CLSID 來識別專案類型。 通常，雖然可以有一個專案的處理站建立單一專案類型的執行個體的一個專案 factory 控點會處理多個專案類型的 GUID。  
  
 與特定檔案的副檔名相關聯的專案類型。 當使用者嘗試開啟現有的專案檔案，或嘗試藉由複製的範本建立新的專案時，IDE 會使用檔案副檔名來決定對應的專案 GUID。  
  
 IDE 判斷是否必須建立新的專案或開啟現有的專案特定的型別，因為 IDE 使用資訊 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] 在系統登錄中找出哪個VSPackage 實作必要的專案 factory。 IDE 會載入此 VSPackage。 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>方法中，VSPackage 必須藉由呼叫和 IDE 中註冊其專案 factory<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A>方法。  
  
 主要方法`IVsProjectFactory`介面是<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>這應該處理兩種情況： 開啟現有的專案，並建立新的專案。 大部分的專案其專案中儲存狀態的專案檔。 一般而言，建立新專案，讓範本檔案的複本傳遞給`CreateProject`方法，然後開啟複本。 現有的專案，會具現化直接開啟專案檔傳遞至`CreateProject`方法。 `CreateProject`方法可以視需要對使用者顯示其他 UI 功能。  
  
 專案可以也使用任何檔案，且，相反地，其專案中儲存狀態檔案系統，例如資料庫或 Web 伺服器以外的儲存機制。 在此情況下，檔案名稱參數傳遞至`CreateProject`方法不是實際檔案系統路徑，而是唯一的字串-URL，來識別專案資料。 您不需要複製範本檔案會傳遞給`CreateProject`觸發要執行的適當建構順序。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)