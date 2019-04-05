---
title: 升級專案項目 |Microsoft Docs
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
ms.openlocfilehash: 04cfbdc9da180dc35278e723da8ce203bdf26ac6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945797"
---
# <a name="upgrading-project-items"></a>升級專案項目
如果您新增或管理您不會實作的專案系統內的項目時，您可能需要參與專案的升級程序。 Crystal Reports 是可以加入至專案系統的項目範例。  
  
 一般而言，專案項目實作者想要運用已經完全具現化和升級的專案，因為他們需要知道哪些參考的專案還有哪些其他專案屬性有進行升級的決策。  
  
### <a name="to-get-the-project-upgrade-notification"></a>若要取得專案的升級通知  
  
1.  設定<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>旗標 （定義於 vsshell80.idl） 在您的專案項目實作中。 這會導致您的專案項目自動 VSPackage 載入時[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]shell 可讓您判斷專案系統正在升級。  
  
2.  宣布<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>透過介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>方法。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>之後的專案系統實作完成升級作業，並建立新的升級的專案，就會引發介面。 此案例中，根據<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>介面之後引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>，則<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>，或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>方法。  
  
### <a name="to-upgrade-the-project-item-files"></a>若要升級專案項目檔  
  
1.  您必須仔細管理檔案的備份程序，專案項目實作中。 這特別適用於並排顯示備份，其中`fUpgradeFlag`的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法會設定為<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>、 側邊的檔案被指定為".old"沿著放置已經備份的檔案。 當專案已升級的系統時間比舊的備份的檔案指定為過時。 此外，它們可能會覆寫除非您採取特定步驟，以避免這個問題。  
  
2.  在您的專案項目取得的專案升級時，通知**Visual Studio 轉換精靈**仍會顯示。 因此，您應該使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>介面，以提供精靈使用者介面升級的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 轉換精靈](http://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [升級自訂專案](../misc/upgrading-custom-projects.md)