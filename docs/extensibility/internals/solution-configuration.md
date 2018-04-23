---
title: 方案組態 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7b2a453d4ea4e8b92b40ee126f9441e6f353606
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="solution-configuration"></a>方案組態
方案層級內容儲存在方案組態。 這些指示的行為**啟動**(F5) 索引鍵和**建置**命令。 根據預設，這些命令會建置，並開始偵錯組態。 這兩個命令的方案組態的內容中執行。 這表示使用者可以預期 F5 來啟動和任何使用中方案透過設定設定的組建。 環境被設計來建置及執行時，最佳化解決方案，而不是專案。  
  
 Visual Studio [標準] 工具列包含 [開始] 按鈕和方案組態下拉式清單右邊的 [開始] 按鈕。 這份清單可讓使用者選擇要在按下 F5 時啟動的組態，建立自己的方案組態，或編輯現有的組態。  
  
> [!NOTE]
>  沒有擴充性介面來建立或編輯方案組態。 您必須使用`DTE.SolutionBuilder`。 不過，有一些擴充性 Api 來管理方案建置。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>。  
  
 以下是實作您的專案類型所支援的方案組態的方式：  
  
-   專案  
  
     顯示目前方案中找到的專案名稱。  
  
-   組態  
  
     提供您的專案類型支援的組態清單，並顯示在屬性頁中，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>。  
  
     [組態] 欄位會顯示要在這個方案組態中建置的專案組態名稱，並列出所有的專案組態，當您按一下箭號按鈕。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A>填寫此清單的方法。 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>方法表示專案支援編輯設定、 新增或編輯選取的項目也會顯示組態標題底下。 每個選取項目啟動呼叫方法的對話方塊`IVsCfgProvider2`介面以編輯專案的組態。  
  
     如果專案不支援的設定，組態 欄位會顯示 無，並已停用。  
  
-   平台  
  
     顯示選取的專案設定，當您按一下箭號按鈕會列出所有可用的平台專案的平台。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A>填寫此清單的方法。 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>方法表示專案支援編輯平台，新增或編輯選取的項目也會顯示標題下的平台。 每個選取項目啟動對話方塊呼叫`IVsCfgProvider2`編輯專案的可用平台的方法。  
  
     如果專案不支援的平台，該專案的平台欄會顯示 無，而且會停用。  
  
-   組建  
  
     指定由目前的方案組態建置專案。 未選取的專案未建置的方案層級建置命令叫用儘管它們包含的任何專案相依性時。 偵錯、 執行、 封裝和部署方案中仍包含未選取要建置專案。  
  
-   部署  
  
     指定與選取的方案組建組態使用 [開始] 或 [部署] 命令時，會部署專案。 核取方塊，這個欄位會使用專案支援藉由實作部署<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>介面上其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>物件。  
  
 一旦加入新的方案組態時，使用者可以選取它從標準工具列組建及/或啟動該組態的方案組態下拉式清單方塊。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [建置專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [專案組態物件](../../extensibility/internals/project-configuration-object.md)