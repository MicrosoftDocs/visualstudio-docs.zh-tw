---
title: 升級專案專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698690"
---
# <a name="upgrading-project-items"></a>升級專案項目
如果您在未執行的專案系統中加入或管理專案，您可能需要參與專案升級程式。 Crystal Reports 是可以加入至專案系統的專案範例。  
  
 專案專案實施者通常會想要利用已經完全具現化和升級的專案，因為它們需要知道專案參考的專案，以及要進行升級決策的其他專案屬性。  
  
### <a name="to-get-the-project-upgrade-notification"></a>取得專案升級通知  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>在專案專案執行的 vsshell80) 中，將旗標 (定義。 當 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell 判斷專案系統正在進行升級時，這會導致您的專案專案 VSPackage 自動載入。  
  
2. 透過方法來建議 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 介面 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> 。  
  
3. 此 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 介面會在專案系統執行完成其升級作業之後引發，而且會建立新的升級專案。 視案例而定， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 介面會在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> 、或方法之後引發 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> 。  
  
### <a name="to-upgrade-the-project-item-files"></a>升級專案專案檔  
  
1. 您必須在專案專案執行中小心地管理檔案備份程式。 這特別適用于並存備份，其中 `fUpgradeFlag` 方法的參數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 會設定為 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> ，而已備份的檔案會放置在指定為 ".old" 的端檔案中。 已備份的檔案若早于升級專案的系統時間，可以指定為過時。 此外，除非您採取特定的步驟來防止這種情況，否則可能會覆寫它們。  
  
2. 當您的專案專案收到專案升級的通知時，仍會顯示 **Visual Studio 轉換向導** 。 因此，您應該使用介面的方法，將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> 升級訊息提供給嚮導 UI。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 轉換向導](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [升級自訂專案](../misc/upgrading-custom-projects.md)