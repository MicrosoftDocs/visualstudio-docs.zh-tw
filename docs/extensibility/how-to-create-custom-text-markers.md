---
title: 如何： 建立自訂文字標記 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc86f6f5e6689903acb4c57131cee5562117f732
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636343"
---
# <a name="how-to-create-custom-text-markers"></a>如何： 建立自訂文字標記
如果您想要建立自訂文字標記，以強調或組織程式碼，您必須採取下列步驟：  
  
-   註冊新文字標記中，讓其他工具可以存取它。  
  
-   提供預設實作和組態的文字標記。  
  
-   建立可供其他處理序進行的服務使用的文字標記。  
  
 如需有關如何將文字標記的程式碼區域的詳細資訊，請參閱 <<c0> [ 如何： 使用文字標記](../extensibility/how-to-use-text-markers.md)。  
  
## <a name="to-register-a-custom-marker"></a>若要註冊自訂標記  
  
1.  建立登錄項目，如下所示：  
  
     **Hkey_local_machine\software\microsoft\visualstudio \\\\<版本 > \Text Editor\External 標記\\\<MarkerGUID >**  
  
     *\<MarkerGUID >* 是`GUID`用來識別要加入標記  
  
     `<Version>` 是的新版[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，例如 8.0  
  
     `<PackageGUID>` VSPackage 的 GUID 實作自動化物件。  
  
    > [!NOTE]
    >  根路徑**hkey_local_machine\software\microsoft\visualstudio \\\\<版本 >** 可以覆寫為其他根目錄的 Visual Studio shell 初始化時，如需詳細資訊，請參閱[命令列參數](../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
2.  建立四個值之下**hkey_local_machine\software\microsoft\visualstudio \\\\<版本 > \Text Editor\External 標記\\\<MarkerGUID >**  
  
    -   (預設值)  
  
    -   服務  
  
    -   DisplayName  
  
    -   Package  
  
    -   `Default` 是選擇性的 REG_SZ 類型項目。 設定時，項目的值是字串，包含一些實用識別資訊，例如 「 自訂文字標記 」。  
  
    -   `Service` 這 REG_SZ 類型的項目包含可提供自訂文字標記所 proffering 服務的 GUID 字串<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>。 格式為 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}。  
  
    -   `DisplayName` 這 REG_SZ 類型的項目包含自訂文字標記名稱的資源識別碼。 格式為 #YYYY。  
  
    -   `Package` 型別 REG_SZ，其中的項目`GUID`服務底下所列的 VSPackage 提供服務。 格式為 {XXXXXX XXXX XXXX XXXX XXXXXXXXX}。  
  
## <a name="to-create-a-custom-text-marker"></a>若要建立自訂文字標記  
  
1.  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 介面。  
  
     此介面的實作定義的行為和外觀您自訂的標記類型。  
  
     這個介面時，會呼叫  
  
    1.  使用者第一次啟動 IDE。  
  
    2.  使用者選取**重設預設值**下方的按鈕**字型和色彩** 屬性頁中的**環境**資料夾，位於的左窗格**選項** 對話方塊將會取自**工具**IDE 的功能表。  
  
2.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A>方法，並指定其`IVsPackageDefinedTextMarkerType`實作應該會根據傳回的標記類型的方法呼叫中指定的 GUID。  
  
     環境呼叫此方法第一次您自訂標記的類型會建立，並指定用來識別自訂的標記類型的 GUID。  
  
## <a name="to-proffer-your-marker-type-as-a-service"></a>若要為服務 proffer 標記類型  
  
1.  呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>。  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>會傳回。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A>方法，並指定的 GUID，識別您自訂的標記類型的服務，並提供您實作的指標<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>介面。 您<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>實作的實作應該傳回的指標<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>介面。  
  
     唯一的 cookie，用來識別您的服務會傳回。 您稍後可以使用此 cookie 來撤銷您的自訂標記型別服務藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>方法的<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>指定這個 cookie 值的介面。  
  
## <a name="see-also"></a>另請參閱  
 [在舊版的 API 中使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何： 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何： 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)   
 [如何： 使用文字標記](../extensibility/how-to-use-text-markers.md)