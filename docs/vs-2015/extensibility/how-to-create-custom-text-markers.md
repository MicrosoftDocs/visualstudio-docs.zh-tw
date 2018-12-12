---
title: 如何： 建立自訂文字標記 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b0a280b44ad468ba44baf81efcc4e4569638e8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783080"
---
# <a name="how-to-create-custom-text-markers"></a>如何： 建立自訂文字標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您想要建立自訂文字標記，以強調或組織程式碼，您必須採取下列步驟：  
  
- 註冊新文字標記中，讓其他工具可以存取它  
  
- 提供的預設實作和文字標記的組態  
  
- 建立可供其他處理序進行的服務使用的文字標記  
  
  如需有關如何將文字標記的程式碼區域的詳細資訊，請參閱 <<c0> [ 如何： 使用文字標記](../extensibility/how-to-use-text-markers.md)。  
  
### <a name="to-register-a-custom-marker"></a>若要註冊自訂標記  
  
1. 建立登錄項目，如下所示：  
  
    Hkey_local_machine\software\microsoft\visualstudio \\\*\<版本 >* \Text Editor\External 標記\\*\<MarkerGUID >*  
  
    <em>\<MarkerGUID ></em>是`GUID`用來識別要加入標記  
  
    *\<版本 >* 是版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，例如 8.0  
  
    *\<PackageGUID >* VSPackage 實作的 automation 物件的 guid。  
  
   > [!NOTE]
   >  Hkey_local_machine\software\microsoft\visualstudio \ 的根路徑\\*\<版本 >* 可以覆寫為其他根目錄的 Visual Studio shell 初始化時，如需詳細資訊，請參閱[命令列參數](../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
2. 建立四個值 hkey_local_machine\software\microsoft\visualstudio \ 底下\\*\<版本 >* \Text Editor\External 標記\\*\<MarkerGUID>*  
  
   -   (預設值)  
  
   -   服務  
  
   -   DisplayName  
  
   -   Package  
  
   -   `Default` 是選擇性的 REG_SZ 類型項目。 設定時，項目的值是字串，包含一些實用識別資訊，例如 「 自訂文字標記 」。  
  
   -   `Service` 這 REG_SZ 類型的項目包含可提供自訂文字標記所 proffering 服務的 GUID 字串<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>。 格式為 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}。  
  
   -   `DisplayName` 這 REG_SZ 類型的項目包含自訂文字標記名稱的資源識別碼。 格式為 #YYYY。  
  
   -   `Package` 型別 REG_SZ，其中的項目`GUID`服務底下所列的 VSPackage 提供服務。 格式為 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}。  
  
### <a name="to-create-a-custom-text-marker"></a>若要建立自訂文字標記  
  
1.  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 介面。  
  
     此介面的實作定義的行為和外觀您自訂的標記類型。  
  
     這個介面時，會呼叫  
  
    1.  使用者第一次啟動 IDE。  
  
    2.  使用者選取**重設預設值**下方的按鈕**字型和色彩** 屬性頁中的**環境**資料夾，位於的左窗格**選項** 對話方塊將會取自**工具**IDE 的功能表。  
  
2.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A>方法，並指定其`IVsPackageDefinedTextMarkerType`實作應該會根據傳回的標記類型的方法呼叫中指定的 GUID。  
  
     環境呼叫此方法第一次您自訂標記的類型會建立，並指定用來識別自訂的標記類型的 GUID。  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>若要為服務 proffer 標記類型  
  
1.  呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>會傳回。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A>方法，並指定的 GUID，識別您自訂的標記類型的服務，並提供您實作的指標<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>介面。 您<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>實作的實作應該傳回的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>介面。  
  
     唯一的 cookie，用來識別您的服務會傳回。 您稍後可以使用此 cookie 來撤銷您的自訂標記型別服務藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>方法的<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>指定這個 cookie 值的介面。  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何： 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)   
 [如何：使用文字標記](../extensibility/how-to-use-text-markers.md)

