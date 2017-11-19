---
title: "如何： 建立自訂文字標記 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ab395fdb8c06e643c76ee0918b8a626abb756cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-custom-text-markers"></a>如何： 建立自訂文字標記
如果您想要建立自訂文字標記強調或組織程式碼，您必須採取下列步驟：  
  
-   註冊新的文字標記中，以便其他工具可以存取它  
  
-   提供的預設實作和組態的文字標記  
  
-   建立一項服務，可供進行其他處理序使用的文字標記  
  
 如需如何適用於文字標記的程式碼區域的詳細資訊，請參閱[How to： 使用文字標記](../extensibility/how-to-use-text-markers.md)。  
  
### <a name="to-register-a-custom-marker"></a>若要註冊自訂標記  
  
1.  建立登錄項目，如下所示：  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<版本 >*\Text Editor\External 標記\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >*是`GUID`用來識別要加入標記  
  
     *\<版本 >*版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，例如 8.0  
  
     *\<PackageGUID >* VSPackage 實作自動化物件的 guid。  
  
    > [!NOTE]
    >  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 的根路徑\\*\<版本 >*會覆寫替代的根 Visual Studio shell 初始化後，如需詳細資訊，請參閱[命令列參數](../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
2.  建立四個值在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<版本 >*\Text Editor\External 標記\\*\<MarkerGUID>*  
  
    -   (預設值)  
  
    -   服務  
  
    -   DisplayName  
  
    -   Package  
  
    -   `Default`是類型為 REG_SZ 的選擇性項目。 設定時，項目的值是字串，包含的一些實用識別資訊，例如 「 自訂文字標記 」。  
  
    -   `Service`這類型為 REG_SZ 的項目包含透過 proffering 提供自訂文字標記服務的 GUID 字串<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>。 此格式為 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}。  
  
    -   `DisplayName`這類型為 REG_SZ 的項目包含自訂文字標記名稱的資源識別碼。 此格式為 #YYYY。  
  
    -   `Package`項目類型 REG_SZ 含有`GUID`服務底下所列的 VSPackage 提供服務。 此格式為 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}。  
  
### <a name="to-create-a-custom-text-marker"></a>若要建立自訂文字標記  
  
1.  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 介面。  
  
     您實作這個介面定義的行為和外觀自訂標記類型。  
  
     這個介面時，會呼叫  
  
    1.  使用者第一次啟動 IDE。  
  
    2.  使用者選取**重設預設值**按鈕底下**字型和色彩**中的 屬性頁**環境**資料夾，在左窗格中的**選項**對話方塊取自**工具**IDE 的功能表。  
  
2.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A>方法，並指定其`IVsPackageDefinedTextMarkerType`實作應該會依據所傳回的標記類型的方法呼叫中指定的 GUID。  
  
     環境呼叫此方法的第一個時間建立時，自訂標記類型，並指定 GUID，識別自訂的標記類型。  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>若要為服務 proffer 標記類型  
  
1.  呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>傳回。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A>方法，並指定的 GUID，識別您自訂的標記類型的服務，並提供您實作的指標<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>介面。 您<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>實作應該傳回指標給您的實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>介面。  
  
     唯一識別您的服務會傳回的 cookie。 您稍後可以使用此 cookie 來撤銷您的自訂標記類型服務藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>介面，指定此 cookie 值。  
  
## <a name="see-also"></a>另請參閱  
 [使用文字標記與舊版應用程式開發介面](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 加入標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何： 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)   
 [如何： 使用文字標記](../extensibility/how-to-use-text-markers.md)