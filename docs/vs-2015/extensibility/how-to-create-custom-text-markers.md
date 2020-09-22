---
title: 如何：建立自訂文字標記 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838784"
---
# <a name="how-to-create-custom-text-markers"></a>如何：建立自訂文字標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您想要建立自訂文字標記以強調或組織程式碼，您必須執行下列步驟：  
  
- 註冊新的文字標記，讓其他工具可以存取它  
  
- 提供文字標記的預設執行和設定  
  
- 建立可供其他進程用來利用文字標記的服務  
  
  如需如何將文字標記套用至程式碼區域的詳細資訊，請參閱 [如何：使用文字標記](../extensibility/how-to-use-text-markers.md)。  
  
### <a name="to-register-a-custom-marker"></a>註冊自訂標記  
  
1. 建立登錄專案，如下所示：  
  
    HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External 標記\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>`GUID`用來識別要加入的標記  
  
    *\<Version>* 是的版本 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，例如8。0  
  
    *\<PackageGUID>* 是執行 automation 物件之 VSPackage 的 GUID。  
  
   > [!NOTE]
   > \\ *\<Version>* 初始化 Visual Studio shell 時，可使用替代的根目錄覆寫 HKEY_LOCAL_MACHINE \software\microsoft\visualstudio 的根路徑。如需詳細資訊，請參閱[命令列參數](../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
2. 在 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External 標記底下建立四個值\\*\<MarkerGUID>*  
  
   - (預設值)  
  
   - 服務  
  
   - DisplayName  
  
   - 套件  
  
   - `Default` 是類型 REG_SZ 的選擇性專案。 設定時，專案的值為包含一些實用識別資訊的字串，例如「自訂文字標記」。  
  
   - `Service` 是類型 REG_SZ 的專案，其中包含服務的 GUID 字串，此服務會依 proffering 提供自訂文字標記 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> 。 格式為 {XXXXXX XXXX XXXX xxxx XXXXXXXXX}。  
  
   - `DisplayName` 是類型 REG_SZ 的專案，其中包含自訂文字標記名稱的資源識別碼。 格式為 #YYYY。  
  
   - `Package` 是類型 REG_SZ 的專案，其中包含 `GUID` 提供服務下所列服務的 VSPackage。 格式為 {XXXXXX XXXX XXXX xxxx XXXXXXXXX}。  
  
### <a name="to-create-a-custom-text-marker"></a>若要建立自訂文字標記  
  
1. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 介面。  
  
     此介面的執行定義自訂標記類型的行為和外觀。  
  
     此介面會在下列情況呼叫  
  
    1. 使用者第一次啟動 IDE。  
  
    2. 使用者會在 [**環境**] 資料夾中的 [字型**和色彩**] 屬性頁下方選取 [**重設預設值**] 按鈕，該資料夾位於從 IDE 的 [**工具**] 功能表取得的 [**選項**] 對話方塊的左窗格中。  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> `IVsPackageDefinedTextMarkerType` 根據方法呼叫中指定的標記類型 GUID，執行方法，指定應該傳回的實作為。  
  
     環境會在您第一次建立自訂標記類型時呼叫這個方法，並指定可識別自訂標記類型的 GUID。  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>將標記類型 proffer 為服務  
  
1. 呼叫的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> 。  
  
     傳回的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> 方法，指定識別自訂標記類型服務的 GUID，並提供介面實作為的指標 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 。 您 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 的實應傳回介面的實作為指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> 。  
  
     識別傳回服務的唯一 cookie。 您稍後可以使用此 cookie 來撤銷自訂標記類型服務，方法是呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 指定此 cookie 值的介面方法。  
  
## <a name="see-also"></a>另請參閱  
 [搭配舊版 API 使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何：執行錯誤標記](../extensibility/how-to-implement-error-markers.md)   
 [如何：使用文字標記](../extensibility/how-to-use-text-markers.md)
